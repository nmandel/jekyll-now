---
layout: post
title: Basic HTML Tricks: Inline Text Elements, Artificial Line Breaks, and Buttons
date: December 6, 2014
---

I have encountered a handful of instances while programming where I need to create some HTML for a page, but it does not need to be a finished product. I am not yet concerned with obtaining a polished look using CSS or various libraries (or perhaps I will never be concerned about this). We are a beginner web developers just looking to get something functional on the page, to be improved later. For some quick and dirty HTML edits, look no further than the following:

One of the questions that would once plague me was: How can I make my text appear on the same line as this other text/link/element? The `<p>`, `<h1>`, `<div>` are all tags that I can insert text into, but each of these will put my text element on a separate line. The solution is the `<span>` tag, which can be used to quickly add an inline text element. Sure enough, `<div>Hello </div><div>World</div>` shows up differently than `<span>Hello </span><span>World</span>`.

Another simple HTML trick has the opposite effect: the `<br>` tag. Simply throw this tag into your HTML to create a line break. Later on, you'll probably be using margins and padding to alter your spacing, but for now, a quick little `<br>` tag should make your primitive HTML page easier on the eyes. Try altering our `<span>` setup from above for a nice visual example: `<span>Hello </span><br><br><span>World</span>`.

Finally, a very useful HTML element is the button. Even if this button won't make it into the final iteration of your product, it can be very useful for testing some sort of user input functionality to be added later. Here is a quick example: `<button id="hello">Hello World</button>`. Here, the text within the button is "Hello World". I've also included an id; this is generally a good idea so that your button can be specifically referred to by id later, particularly if there are more buttons that will be added.