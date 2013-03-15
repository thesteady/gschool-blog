---
title: HTML and CSS Reading Review,HTML Section
date: 2013-03-11 15:17 -06:00
tags: reading
---

Since we're starting to program web applications in class, it was most appropriate that this week we started reading Jon Duckett's _HTML and CSS: Design and Build Websites_. The first section was an overview of HTML basics (and a bit more). I spent some time last fall learning HTML, so a lot of it was review for me. I did enjoy the review, though, and was happy to pick up some new tips.

####Horizontal Line Rules

First off, I don't think I have ever used horizontal line rules, which get coded like this:

```html
<hr>
```
The result looks like this:

* * *

_(it's faint in my current formatting, but it's there!)_

####HTML Forms

The topic I really enjoyed learning about was forms, since I am sure that I will be using them in the future. Forms are a way for a user to interact with your website. For example, maybe you are collecting information from a user, or allowing them to search for things on your site. There are a variety of form options available in HTML, including text inputs and boxes, check boxes, and submit buttons.

Here is the HTML for radio buttons:

```html
<form>
  <p>Here's a few radio buttons!
  <br>
  <input type="radio" name="buttons" value="1" />Button 1
  <input type="radio" name="buttons" value="2" />Button 2
  <input type="radio" name="buttons" value="3" />Button 3
  </p>
</form>
```

And _here_ is what that looks like on the web:

* * *

<form>
  <p>Here's a few radio buttons!
  <br>
  <input type="radio" name="buttons" value="1" />Button 1
  <input type="radio" name="buttons" value="2" />Button 2
  <input type="radio" name="buttons" value="3" />Button 3
  </p>

</form>
* * *

Fun! Now, in most cases you would set up a way to actually make those radio buttons meaningful, such as by sending the choice to a server (via PHP, perhaps) and causing that choice to affect what happens next on the website, or recording that choice for later use. Now I know how to at least do the front-end work!
