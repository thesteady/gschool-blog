---
title: Reconciling With Middleman
tags:
---

This blog, and most of the other gSchoolers' blogs, are being created with Middleman. By cloning a git repo set up by our teachers, it was easy to start writing articles and get them on the web via Heroku. As long as I just wanted to write some text articles with markdown, and maybe add a few ```code samples``` here and there, Middleman a la' gSchool was fine. Unfortunately, customizing layout and style was a different matter.

Up until now, if you had asked me my thoughts on this tricked-out blog engine, I wouldn't have given you a very nice answer. Armed with a minimal understanding of HTML/CSS, a growing knowledge of Ruby, and absolutely no Rails experience, wading through the folders provided by the Middleman set up was a bit mindboggling for me. Everytime I waded into the CSS or layout files to attempt to make tweaks, it ended in a hairy mess and less-than-satisfactory results. Boo.

Over the past few weeks we read Jon Duckett's HTML and CSS and started working in Rails. Lightbulbs started to go off -- slowly. I tried making some edits to my blog and had moderate success in changing colors and fonts, but struggled to figure out how to override a lot of the built in CSS and SASS styling. Having seen a Rails application folder/file structure made Middleman's structure less chaotic. I think I get it now (mostly). Last week's homework assignment was to build a static [resume](/resume.html) page for our site. This pushed me to do two things:

1. Dig through the config file and layout files
2. Realize that it would be easiest for me to write separate layout and CSS files for the resume page.

Writing the layout file from scratch proved to be enlightening, as well. HAML had been a bit intimidating before, but once I slowed down and paid attention to it, and putzed around with it for a bit, things started clicking. I really like the ease with which you can create ne divs and assign classes. No more wading through all those ``` </div>```s everywhere.

Writing my own CSS file was a fun experiment, too, and I learned a few tricks. I have plans in the works (including a git branch!) for a total redesign of my blog layout and style. It's going to be awesome, but will probably take me a while to get it into working state. I am going to completely remove the provided layouts and styling, and go it my own. Woot!

So, while I'm not convinced that Middleman is awesome, I'm okay with it now.
