---
title: Reading HTML and CSS, CSS Section
tags: reading
---

This week our reading was the second section of Jon Duckett's _HTML and CSS_, all about CSS. My blog has been downright ugly since my first botched attempt to customize it, so I definitely enjoyed reading up on using CSS to style my site.

#### Old Version of Site == Not Very Pretty
<img src="/images/blog/old_site.jpg" alt="old site" title="Old Site" />

One of things that has been holding me back from changing things up has been understanding CSS inheritance. Our blog template (we're using middleman) came with a pre-filled CSS stylesheet with lots of things I didn't understand. After doing my reading and looking back at the stylesheet, things definitely made more sense. One thing I realized was that a lot of the CSS wasn't even being used in my blog! Cleaning up my stylesheet a bit helped me prepare for a first draft re-style.

My next step was to think about what I really wanted to change. I prioritized them like so:

1. Overall color scheme
2. Sidebar color scheme and details
3. Title styling

In the process of doing this, I was supposed to use at least three techniques I'd read about in _HTML and CSS_, and discuss them here in this article.

#### Creating a New Color Scheme

Did you see my old color scheme? If not, check out the picture above. I liked the light and dark greens, but somehow had managed a green-to-pink gradient for each of my blog article boxes on the main page. Eek. That had to go. For lack of creativity, I decided to start with some greyscale, with the hopes of adding more color later. I also had to find where that awful pink was being declared in my CSS file. Using Chrome's "Inspect Element" tool was helpful in figuring it out. It turns out there was a gradient setting, buried in the CSS:

```css
div.panel {
  background: #CCE0D1;
  background: -moz-linear-gradient(top, #CCE0D1 0%, #dedede 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, #CCE0D1), color-stop(100%, #dedede));
  background: -o-linear-gradient(top, #CCE0D1 0%, #dedede 100%);
}
```

Now, if you have your hex colors memorized (... you don't?) you'll find that #CCE0D1 is the light green that I set at some point, and #dedede is _NOT_ pink -- it's a light grey. But, because there was a gradient being applied, it created a pink effect. After some playing with different color schemes, I settled on a light blue background, some yellow gradient for the article boxes, and brown text. I tried to pick colors so that the text was a moderate contrast with the background... something that would be readable. I'm not completely satisfied with it, so I'll probably change it again soon.

In the process of changing the text to brown, I realized that a secondary CSS file in the middleman stylesheets, called app.css.scss, mystically imports a great deal of the styling from elsewhere. I haven't fully figured out how this works, so some of my text is still black when I want it to be brown.

#### Restyling the Sidebar

<img src="/images/blog/old_site_sidebar.jpg" alt="old site sidebar" title="Old Site Sidebar" />

That white and blue box really drove me nuts. I also decided I wanted to have a light border around the non-selected tab, to make it more obvious that it was something a viewer could click.

#### Restyling My Blog Title

3. Make the title of my blog stand out and be more than just some quickly written text.



Next week's reading will discuss layout design. Look for a new layout then!
