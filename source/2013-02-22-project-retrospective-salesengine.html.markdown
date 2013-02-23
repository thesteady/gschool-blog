---
title: Project Retrospective -- SalesEngine
date: 2013-02-22 09:24 -07:00
tags: project
---
Yesterday we turned in our SalesEngine project for gSchool. This was a two week project building an API system to query a set of fake merchant, customer, invoice, and item data, complete with credit card transactions. We worked on SalesEngine in pairs -- a new experience for me. 

My project pair, Elaine, and I worked on some parts together, and split other sections of the project up to work on our own. I think this mix worked out pretty well. I learned a lot just by seeing someone else's coding style, and figuring out how to make it work with my own. It was nice to have a second set of eyes to catch typos, missing "ends", and methods that could be written more eloquently. Because our project would be evaluated based on our testing coverage, we focused on Test Driven Development. 

One of the sections I worked on mostly by myself was business intelligence methods for merchants. A required function of this section was that a method could be called to return a sorted list of the top merchants by their revenue total. My initial write-up of this method looked like:

```ruby
 def self.most_revenue(x)
    sorted_merchants = merchants.sort do |merchA, merchB|
      merchB.revenue <=> merchA.revenue
    end
    sorted_merchants.take x
  end
  ```

#####What does this code do?

At the broad level, it's sorting all of the merchants in the database (csv files, really) based on their calculated revenue. More specifically, it does something like this:

>1. Calculate merchant A's revenue.
>2. Calculate merhant B's revenue.
>3. Compare and sort them highest to lowest.

The next step is important:

>4. Take the next set of merchants: B and C.
>5. Calculate merchant B's revenue, _again_.
>6.Calculate merchant C's revenue.
>7. Compare and sort them.


So, essentially, this code is calculating the revenue for each merchant at least twice. It's also important to note that each time a revenue is calculated, the code actually has to go through several steps:

>A. Gather the invoices for a merchant.
>B. Check that the invoices are successful
>C. Calculate the subtotal (quantity x price) for each item on the revenue.
>D. Create the invoice subtotal.
>E. Add all of the invoice subtotals together to finally find the merchant's revenue.


This is quite a calculation intensive process, and so calculating it more than once for any merchant really slowed our processing down. At this stage, the test for _just_ this method took between 20-30 minutes. Not only was the long waiting time annoying, this method was violating the Single Responsibility Principle we learned about in class.

#####I knew there had to be a faster, better way to do it.

I envisioned being able to calculate each merchant's revenue, store it somehow, and _then_ run the comparison, but I wasn't really sure how to go about doing it.

Luckily, on Tuesdays gSchool has a group of awesome volunteers come in and help us with our code. Elaine and I met with Cory Flanigan, and I asked him about my redundancy conundrum. We first walked through the steps and memo-ized many of the value collections, so that they shouldn't need to be recalculated if they already existed. Next, we found a way to get rid of the extra merchant revenue calculations. Cory suggested storing the merchant ID and revenue values in a hash so that they could be quickly called during the sorting.

With Cory's help, our code ended up looking like this:

```ruby
def self.most_revenue(x)
  
  merchants_with_revenue = merchants.each_with_object({}) do |merchant, hash|
    hash[merchant.id] = merchant.revenue
  end.sort {|(id_a, rev_a), (id_b, rev_b)| rev_b <=> rev_a }.take(x)

  merchants_with_revenue.map do |arr|
    self.find_by_id(arr[0])
  end

end
```

This is all nice, but how much did it really optimize the code? **Answer: a lot**. Instead of running this test in 20-30 minutes, it now runs in about 60 seconds! Still a little bit of time, but much more doable. By the end of the project, our full test suite (in MiniTest) ran at about 4.5 minutes. Not too bad! If I had had time to optimize it more, I think I would have enjoyed looking for ways to pre-calculate other things like invoice item subtotals and even invoice subtotals. 

Working with Elaine and Cory to optimize the merchant revenue test was a great learning experience for me. It taught me to think more critically how methods I write are being processed, even before I write those implementations. It also made me more aware of just how many different ways things can be done in Ruby. 

Check out our [Project Repository on GitHub](https://github.com/thesteady/sales_engine) -- I'd love comments/feedback/suggestions!
