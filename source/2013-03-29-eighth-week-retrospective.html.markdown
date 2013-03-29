---
title: Eighth Week Retrospective
date: 2013-03-29 09:00 -06:00
tags: retrospective
---

####Rails Thoughts
Working in Rails is cool. Seing our StoreEngine project coming together through all the models, controllers, and views is pretty amazing. I think what impresses me the most is how easy it can be to create new pages that load differently depending on what data is there (e.g., a table of all the orders that belong to a particular customer, depending on who is logged in).

It's also pretty cool that you can customize your link paths. In our project, for example, we're creating views specific to the user. We didn't want the user's ID to be in the link, though, so we changed it!  This cool piece of trickery is also one of the most confusing for me, I think. I don't totally understand how to create exactly the url path that I want, and get it to go to the place I want it to, so doing this takes me some experimenting. Part of it is just being unfamiliar with the language of doing this, and part of it is understanding the divvying up of responsibilities among controllers. For instance, when I wanted the user to be able to view their orders, the natural path that Rails suggested for me to use was orders#show. I struggled against this for a while, thinking that loading this view should somehow be taken care of by the user controller.


####Working in Larger Teams

This is our first project working in teams larger than pairs. I am in an awesome team of three(Logan, Raphael, and me). We've worked hard to communicate effectively and be concious of what each person is working on, which has made splitting up work and merging branches a breeze. I think our careful communication and frequent check-ins, along with the use of PivotalTracker, has enabled us to sail through the basic project requirements. I think our personalities, working, and coding styles are all meshing together really well, which definitely helps, too. I definitely am not taking it for granted -- I can imagine how much more difficult this project would be if we weren't working so well together.

For the upcoming week, we will be tackling extensions and getting layout and design locked in. Logan has been designing detailed wireframes in Balsamiq, which I am looking forward to playing with, too.

I can't wait for our demo next week -- our site is going to be slick!


####Hacking Outside of Class

This week I attended a Hackfest at [Quickleft](http://quickleft.com/), a design and development company up in Boulder. The theme was Rube Goldberg Machines, and the goal was to create a "machine" that used a combination of devices (e.g., Sonos speakers, arduino boards, proximity tags, wireless-controlled electical switches for lights, etc) and even streaming Twitter data (thanks to Gnip) to do something creative. I really enjoyed playing with the PowerTrack stream from Gnip, especially seeing how that data comes in and how you can parse it. I also enjoyed helping a team out with using the Dino gem for using arduino for ruby (Thanks, Blair!). I had a great time, learned a bit, and met some really cool people.
