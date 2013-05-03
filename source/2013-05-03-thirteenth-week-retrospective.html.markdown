---
title: Thirteenth Week Retrospective
date: 2013-05-03 09:05 -06:00
tags: retrospective
---

This week's highlight of events:

* Guest Speakers David Heinemeier Hansson and the authors of Learning jQuery, Karl Swedberg and Jonathan Chaffer
* Wrap-up and Demo of Daughter of Store Engine Project
* Geospatial Meetup hosted by Peter Batty, Nate Irwin, and Jason Sanford.

#### Project Thoughts -- Daughter of Store Engine

Yesterday we wrapped up the Daughter of Store Engine Project. My team had the task of building features related to reviewing and rating products. I think our project came out well, in part to less stress about meeting a large stack of specifications, a better git workflow, strong communication in the team, and a better focus on test driven development (TDD).

Kyle and I spent most of the project pairing together. It was a lot of time working with another person, but it never felt forced or stressful. We did a good job of working together and taking advantages of each other's strengths.

I had fun playing with and implementing some jQuery. I was particularly satisfied with a feature we implemented: when a user clicks a 'Flag Comment as Inappropriate' link, it posts data to the database (to flag the comment) and removes that comment from the page without a refresh. I think it startled some classmates to see it just disappear! This is what the jQuery code looks like:

```
$(document).ready(function() {
  $('.flag a').click(function() {
    var review_div = $(this).closest('.review');
    var the_link = $(this).parent();
    var store = review_div.data('store');
    var product_id = review_div.data('product-id');
    var review_id = review_div.data('product-review-id');

    var post_path = "/" + store + '/products/' + product_id + '/reviews/' + review_id + '/flag?status=flagged';

    $.ajax({
      type: "POST",
      url: post_path,
      context: '.flag a' ,
      success:function(){
        $(the_link).closest('.review').hide();
      }
    });
    return false;
  });
});
```

If we had another two weeks to work on this project, I think we could make it truly awesome! I would love to have had more time to spend polishing the layout and design -- we left it mostly to the last minute. I would also like make a few features more user-friendly and implement more jQuery ajaxy techniques.


Check out the code on [GitHub](https://github.com/kylesuss/daughterofstore_engine)!

#### Looking Ahead

This project helped me feel a lot more comfortable with controller testing. I also think I improved my skills in refactoring and writing cleaner code to start with, although I want to work on those two things more.

Our next project is going to be API-intense. I am excited! I think the next project will be challenging, since it will be a different focus than what we've been doing so far. I have been playing around a bit with a few APIs for Open Source projects, and want to understand what I'm doing more fully, and know how to do what I want to with them.

Last night I went to a new Geospatial Meetup here at Galvanize. It was a great group of people and awesome talks. I was excited to see what people are doing in the web mapping space. I'm hoping I can incorporate some slick web maps into a future project for gSchool.

I'm still not sure exactly what kind of job I want to have when I finish gSchool. I enjoy the front-end work, but don't feel as confident with it as I do back-end. Hopefully I can do more work with it on my next project. I also really enjoy the back-end work.

