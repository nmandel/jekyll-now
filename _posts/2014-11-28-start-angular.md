---
layout: post
title: Start using Angular
date: November 28, 2014
---

You may have heard of AngularJS, which is a framework put forth by Google that is geared toward single-page web applications. Getting started with a new framework is always a daunting task, so if you are looking for a kicking-off point, here it is: we will create the simplest possible web app using AngularJS.

First, we want to include the Angular library in our code. Start by creating a basic index.html file for a blank webpage. From there, you can either download angular so that you can work offline, or simply source the following URL in your HTML:

https://ajax.googleapis.com/ajax/libs/angularjs/1.0.7/angular.min.js

This will pull the necessary scripts straight from the Google CDN (content delivery network), so you don’t need to install anything.

Next, we want to create a JavaScript file where we will keep our logic; let’s call it app.js. Then, go ahead and source the app.js file in the HTML. So far, the HTML page should look something like this:

```
<!doctype html>
<html ng-app="sampleApp">
   <head>
     <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.0.7/angular.min.js"></script>
     <script src="app.js"></script>
   </head>
   <body>
   </body>
</html>
```

In order to get some functionality for our app, we will need to create a controller; in Angular, controllers are housed within modules (which will also house various other parts of a more complicated app). So, let us instantiate our module and add a controller in the app.js file:

```
angular.module('sampleApp', [])
   .controller('sampleController', function($scope) {
     $scope.words = "Hello world!";
   });
```

Here, the first argument to ‘module’ is ‘sampleApp’, which is what we will call our app. The second argument is an array of models that this model is dependent on; in this case, there are none as of yet. We create our controller, dubbed ‘sampleController’, as a method of the ‘sampleApp’ module. Each controller in Angular comes with its own scope, which is delineated by the $scope keyword. When we set $scope.words, we can reference ‘words’ by itself as long as we are within the scope in question. The syntax we use for this is a double curly-brace, so that we can add the following to the HTML:

```
<div ng-controller='sampleController'>
   <h1>{{words}}</h1>
 </div>
```

And that’s it! Your webpage should display the words “Hello World!” in nice large letters (thanks to the `<h1>` header tag). You are ready for your Angular app to blossom into something remarkable. The documentation is good, so with this jumping-off point and a bit of experimentation, you’ll be amazed at the functionality you can accomplish in relatively few lines of code.