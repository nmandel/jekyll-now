---
layout: post
title: Check database for preexisting username on input field focus change
date: January 28, 2015
---

Recently I have been working on a project called Icecomm (http://icecomm.io), which simplifies WebRTC for developers. One interesting UX challenge that I undertook as a part of the project was a part of the sign up process: when the user entered their desired user name and shifted focus to the next field, I wanted the database to be queried right then to check if they had entered a unique user name, and respond with an error message if not.

For a bit of background on the technologies used: we had an Anuglar.js front-end, with a Node/Express server and a MongoDB (using Mongoose and Mongolabs) database- all adding up to a MEAN stack.

The HTML for the username field looked something like this:

```
{% raw %}
<input type="text" name="username" placeholder="Username" 
  ng-blur="validate=true; checkUniqueUserName()" 
  ng-model="username" />
<small class="error" ng-show="usernameAlreadyExistErrorMsg">
  {{usernameAlreadyExistErrorMsg}}
</small>
{% endraw %}
```

The trick here is Angular's ng-blur, which is activated when the focus switches from the input field in question. The checkUniqueUserName function that is then called looks like this: 

```
$scope.checkUniqueUserName = function() {
  $http.post("/checkUsernameExists", {
    username: $scope.username
  })
  .success(function(data) {
    if (data.alreadyExisting === true) {
      $scope.usernameAlreadyExistErrorMsg = "Not a unique user name!";
    }
    else {
      $scope.usernameAlreadyExistErrorMsg = "";
    }
  })
}
```

A post request is sent to the server with the entered username as a parameter, and the server will send back a value of 'true' or 'false' in the 'alreadyExisting' parameter of the returned data. Here is the code on the server end:

```
app.post('/checkUsernameExists', function(req, res) {
  var username = req.body.username;
  var alreadyExisting = {};
  alreadyExisting.alreadyExisting = true;
  User.findOne({username: username}, function(err, foundUser) {
    console.log('foundUser', foundUser);
    if (!foundUser) {
      alreadyExisting.alreadyExisting = false;
    }
    res.send(alreadyExisting);
  });
});
```

Finally, "User" is a MongoDB schema, and findOne is a built-in function that finds all of the pieces of data where the username is equal to the name in the input field- and thanks to our handy checker, there will never be more than one piece of data returned. 

So, if the user already exists in MongoDB, alreadyExisting is set to 'true' and sent back to the front-end, where the 'if' statement generates an error message in the 'usernameAlreadyExistErrorMsg' variable. Then, the HTML checks if there is any message inside the 'usernameAlreadyExistErrorMsg' variable; if there is, then the error message is displayed- all before our user has even gone on to type the first character in their email address.

The methods used here can be extended to a query to the database for emails as well. Just be sure to also check the database when the user clicks "sign up" as well! Finally, I would not recommend including this feature on a login page, because it has the potential to make a hacker's job easier (checking a high volume of usernames would become a quicker process). Happy authing!