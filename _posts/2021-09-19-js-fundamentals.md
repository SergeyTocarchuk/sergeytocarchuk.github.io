---
layout: post
title: "JavaScript: Fundamentals"
author: "Serhii T."
categories: journal
tags: [js,fundamentals]
image: 
---

### Variables: Name Things Right

let vs var vs const:
- variables declared using **const** cannot be reassigned.
- **let** === **var**

### DOM

One of the most unique and useful abilities of JavaScript is its ability to manipulate the DOM.

In the [article](https://www.theodinproject.com/paths/foundations/courses/foundations/lessons/dom-manipulation) you can find answers for the following issues:
- Explain what the DOM is in relation to a webpage.
- Explain the difference between a “node” and an “element”.
- Explain how to target nodes with “selectors”.
- Explain the basic methods for finding/adding/removing and altering DOM nodes.
- Explain the difference between a “nodelist” and an “array of nodes”.
- Explain what “bubbling” is and how it works.

##### Adding Text Content && Adding HTML Content

```
div.textContent = 'Hello World!'                               
// creates a text node containing "Hello World!" and inserts it in div

div.innerHTML = '<span>Hello World!</span>';                   
// renders the HTML inside div
```

Note that **textContent** is preferable for adding text, and **innerHTML** should be used sparingly as it can create security risks if misused. Check out [this video](https://www.youtube.com/watch?v=ns1LX6mEvyM&ab_channel=WebDevSimplified) if you want to see an example of how.

### Applying JavaScript to HTML

The ```<script>``` element should also go into the head, and should include a _src attribute_ containing the path to the JavaScript you want to load, and defer, which basically instructs the browser to load the JavaScript after the page has finished parsing the HTML. This is useful as it makes sure that the HTML is all loaded before the JavaScript runs, so that you don't get errors resulting from JavaScript trying to access an HTML element that doesn't exist on the page yet. There are actually a number of ways to handle loading JavaScript on your page, but this is the most foolproof one to use for modern browsers

[MDN article](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#applying_css_and_javascript_to_html) for more detailed information

### Adding Inline Style

See section on [CSS Style rules](http://domenlightenment.com/#6.2) for more info on inline styles.