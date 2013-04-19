---
title: Eleventh Week Retrospective
date: 2013-04-19 08:10 -06:00
tags: retrospective
---

#### More Cache, Less Load Time

This week I learned about optimizing and caching web pages for faster load times. I used New Relic locally to watch the load speeds and how they changed after each tweak of the code and to identify how many SQL queries were being carried out on page load. It was really satisfying to use this tool to find places to optimize and speed up. For example, one page loaded a table of all the products in a store. It turns out that a SQL query was being run for EACH product. At the time I looked at this page, that meant 110 SQL queries. With Katrina's help, I optimized that page, in part, by using   ``` store.includes(:products)```  . This dropped the number of queries to about 6 -- most of which were for other parts of the page. Memoizing instance variables so that queries didn't always need to be re-run also helped things.

I also worked on some page fragment caching. By saving fragments of pages that didn't change much (or ever) in our application, I was able to speed up page loads. At first, I wasn't sure it would make much difference. Caching our site logo (which NEVER changes), for instance, barely made an impact on speed, but once I had cached other small pieces and some larger ones, too, things definitely paid off. Fragment caching got me working a little bit more with redis, which I think I will enjoy learning more about.

#### Time Tracking

For the past two weeks, I've been tracking my school time using a trial account of Harvest. I thought it might be interesting to see what I actually spend the most of my time working on, but the results weren't really surprising. Most of my time was spent working on the project. Out of 70 hours I tracked over the past two weeks, over 62 were dedicated to project work.

I do like using Harvest, though, and would definitely consider using it in a work or consulting situation. The design is clean, it's easy to use, and once I got a little used to it, easy to remember to do.
