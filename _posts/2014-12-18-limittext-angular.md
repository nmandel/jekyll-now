---
layout: post
title: Limit characters displayed in text with Angular
date: December 18, 2014
---

Our goal is to limit the amount of characters shown in a block of text using angular. In the aim of brevity and simplicity, let’s assume that we have a large chunk of text in a model called ‘text’, and we only want to show 150 characters at a time, with the option to expand our view to see the entire block of text. If we were to include the text without any limit, it would look like this:

```
{% raw %}
{{text}}
{% endraw %}
```

To display only the first 150 characters, the code changes as follows:

```
{% raw %}
{{text | limitTo: 150}}
{% endraw %}
```

That’s simple enough. But, now we have no way to view the rest of our text. To do so, we are going to need to initialize a limit value in an outer element so that we can later modify it:

```
    {% raw %}
<div ng-init="limit = 150">
    {{text | limitTo: limit}}
</div>
    {% endraw %}
```

If the length of the text is greater than the limit (meaning we have cut off some text), we want to add an option to show more text:

```
    {% raw %}
<div ng-init="limit = 150; moreShown = false">
    {{text | limitTo: limit}}
    <a ng-show="text.length > limit"
       href ng-click="limit=text.length; moreShown = true">  More
    </a>
</div>
    {% endraw %}
```

Here, we are also initializing a variable that will track whether or not our full block of text is displayed. If the length of the text is over the limit, ng-show will active and the href displaying a clickable “More” will appear. On click, the limit will be set to the length of the text so that the entire block is displayed, and moreShown will correctly track the change to say that all the text is displayed.

Now, maybe we would like an option to shorten our text once again. We can use a similar sort of logic to add a “Less” href- just add the following code to the above:

```
<a ng-show="moreShown" href ng-click="limit=150; moreShown = false"> Less </a>
```

The ng-show will trigger if we have the full amount of text displayed, and on click, the text limit will go back down to 150, with moreShown getting set back to false.

Finally, we can throw in some logic to add an ellipses for concatenated text; our final code will look as follows:

```
    {% raw %}
<div ng-init="limit = 150; moreShown = false">
    {{text | limitTo: limit}}{{text.length > limit ? '...' : ''}}
    <a ng-show="text.length > limit"
      href ng-click="limit=text.length; moreShown = true">  More
    </a>
    <a ng-show="moreShown" href ng-click="limit=150; moreShown =    false"> Less </a>
</div>
    {% endraw %}
```