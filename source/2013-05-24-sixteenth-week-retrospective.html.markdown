---
title: Sixteenth Week Retrospective
date: 2013-05-24 14:46 -06:00
tags: retrospective
---

#### Project Thoughts: FeedEngine

This week we wrapped up FeedEngine, a project intended to consume multiple APIs. My group worked on a photo-focused project (the oh-so-creatively-named Photoline) and integrated with Flickr and 500px. It was an interesting project to work on and I learned a lot -- not just about APIs, but about subdomains and background workers, too (and a bit of jQuery!).

While I wish we had been able to get more done with our project, especially in terms of front-end pizazz, I am pretty happy with the solidness of the back-end portion. I spent quite a bit of time refactoring our initial API integration to be abstracted out from the rest of our code so that none of the main objects (e.g., feeds, searches, feed items )knew about interacting with the API. This made it easy to integrate with our second API, 500px. It also meant that we genericized (is that a word?) results from both APIs into one type of object, which made it easy to manipulate and call from controllers and display in views. This process definitely taught me a lot about working with APIs.

I implemented subdomains for Photoline, which was a new concept for me. We decided that when a user created a new 'feed' (a collection of photo searches from one or more sources), they would have a subdomain for that feed, so that they could share it, link it, and easily return to it later. Implementing subdomains with rails has a few consequences: you have to adjust how you browse to your site in development mode, you have to carefully hooking up some environment and routing settings, and, a trick: you can't do it on a free, generic heroku app (e.g., photoline.herokuapp.com) -- it has to be from your own domain name. After struggling through subdomains a bit, I feel like I understand them a lot more clearly now, so am glad I tackled it.

I also implemented background workers with resque and resque-scheduler.
And the jQuery to slide photos up and down on the feed page:

```
$(document).ready(function(){
  //This loads the first image to show on the FEEDS SHOW page
  $('.show-photo').first().toggleClass('hidden');

  // When user clicks the 'next' button, the next next photo
  //gets turned on, slides up, and the current photo turns off
  $(".slideup").click(function(){
      var photo = $(this).closest('.show-photo');
      $(photo).next().toggleClass('hidden');
      $(photo).slideUp(500, function(){
          $(photo).toggleClass('hidden');
      });
   });

  // When user clicks 'previous' button, prev photo shows,
  // slides in, and current photo hides
  $(".slidedown").click(function(){
      var photo = $(this).closest('.show-photo');
      $(photo).prev().toggleClass('hidden');
      $(photo).prev().slideDown(500, function(){
        $(photo).toggleClass('hidden');
      });
   });
});
```

Check out the code on [GitHub](https://github.com/pnblackwell/feed_engine)!
