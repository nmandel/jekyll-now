---
layout: post
title: Chatbuilder
---

Welcome to my first blog post! As of right now, I am in my first week of an accelerated programming school (coding bootcamp) known as Hack Reactor. There are many things that I have learned and experienced this past week that I could speak to, but I thought instead I would look back to a Hack Reactor project I completed before I was even accepted into the program. After venturing a few steps in to the Hack Reactor application, I was greeted with a difficult project whose completion was not required, but recommended before entry into the program. I would encourage anyone who is thinking of applying to the program (or anyone simply looking for a coding challenge) to complete Chatbuilder as both a learning experience and indicator of future success.

Chatbuilder can best be described as a simplified version of a twitter feed, whose implementation requires some knowledge of DevTools, JavaScript, jQuery, and HTML. I was new to most of these concepts coming in to the project, but by the time I was finished, I felt much more comfortable with all of them thanks to this valuable exposure. To illustrate this effect, I’ll provide an example of a very short function from my project:

```
function addMsg (msg) {
  $(".messages").append("<li>" + msg + "</li>");
}
```

In order to reach a point where I had the ability to write such a function, I first had to gain some level of understanding of jQuery (represented by the “$” symbol) and its interaction with HTML DOM elements (referenced with “.messages” and “li”). The function itself is in JavaScript, which I had some experience with from various lessons and coding challenges. This particular function is meant to be called whenever a message should be displayed (either through timed computer-generation or user input). The function takes a string as input and adds it to the DOM as an “li” element, which is then displayed as a line on the page.

My intention in writing this post is to recommend an avenue for learning about some web developing technologies and preparing oneself for the intense curriculum offered at Hack Reactor. The Chatbuilder project has enough instruction such that I was prevented from becoming overly lost or off-track, but the learning curve was still relatively steep as I was made to figure out most of what I needed for myself. Good luck, gentle reader!

<!-- ![_config.yml]({{ site.baseurl }}/images/config.png) -->
