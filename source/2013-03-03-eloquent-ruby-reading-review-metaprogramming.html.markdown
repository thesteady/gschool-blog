---
title: Eloquent Ruby Reading Review, Metaprogramming
tags: reading
---

####That's So Meta

Before reading the Metaprogramming section of Eloquent Ruby, I honestly wasn't sure what metaprogramming even was. I knew that metadata is essentially data about data (I spent _months_ writing XML metadata for a job once), but how could you program about programming? Program your programs? Hmm. Luckily, Russ Olsen did an excellent job of explaining Ruby metaprogramming in just 83 pages. While I'm not sure that I would use some of the metaprogramming techniques presented, there are some that I thought were pretty cool.

I liked the metaprogramming way of including both instance and class methods in a module. Basically, modules can usually have either instance methods (which you _include_ in a class) or class methods (which you _extend_ in a class). But what if you have a module with mostly instance methods, and you suddenly need a few class methods? With metaprogramming, you can use the ```self.included()``` method which lets a module or class know when it has been included in another module or class. You can then tell the inclusive module/class to _extend_ the rest of the methods. Pretty neat!

####Method_Missing

Olsen spends several of the Metaprogramming chapters discussing ```method_missing```. It's an interesting and versatile way to catch potential errors in your program and (hopefully) attempt to keep things from crashing. Olsen explains that method missing already exists in the ```Object``` class, but that, like other methods, you can overwrite it (p265). Used properly, it could give you a chance to send your program users a message when they type in something incorrect, but if done incorrectly, it could cause major problems (like infinite loops).

>I certainly wouldn't want a "method_missing kerfuffle" to find myself "off [...] onto an all-expenses-paid trip to infinite recursion land" (p271).

####Final Thoughts On _Eloquent Ruby_

Overall, I think this is a great book. While I did not understand many of the things I read enough to actually try implementing them, I can see that _Eloquent Ruby_ will be a nice resource to pick up again when I have more experience working with Ruby.
