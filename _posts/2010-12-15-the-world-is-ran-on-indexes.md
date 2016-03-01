---
id: 1547
title: The world is ran on indexes!
date: 2010-12-15T23:00:36+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1547
permalink: /the-world-is-ran-on-indexes/
link:
  - 
categories:
  - Programming
---
An index might be a strange word to some people. Generally it means a list of items that all have certain properties. If you were to create a list of all the cities in the world, you would have an index of cities. If you look in the back of a book, you would find an index of subjects covered in the book. All of these indexes are lists of items that have common properties (being a city, being a subject in a book, etc).

Indexes are extremely useful things while programming. Let&#8217;s say I had a list of 10,000 recipes. Let&#8217;s say then that every time someone ran our program, they would type in an ingredient and the program was suppose to spit out all of the recipes that contained that ingredient. Going through all 10,000 recipes every time would be inefficient, especially if you know that it is the same 10,000 recipes and the results won&#8217;t be different tomorrow or the next day. In this case, indexes give us enormous power to cache results so that we can minimize just how many times we go through the list.

_To create an index for this data, you would run through the 10,000 entries of data and find all of the item that contained onions, or whatever ingredient you are looking for. Then, you would store all of the recipes that you just found in a separate list. This list has become your index of onion recipes. Now if anyone ever asks for the list again, you can use the index instead of the original data and you save a lot of time and energy._

However, there are even more interesting ways to use indexes to make your data lookup easier. Take a basic blog dataset: a list of posts with title, date, and content. Let&#8217;s say you needed to display a list of posts with the post&#8217;s title and date. One way of doing this would be to go through your original data and take out the title and date and display it on screen, but we need efficiency here!

A more efficient way to keep the data stored is through an index that only contains the information you need. If all you need to do is display post titles and dates, you can create and store an index with only the post titles and dates. That way you don&#8217;t have to deal with the content or any other fields you might have that are completely irrelevant to what you want to do.

Let&#8217;s step this up one more time. Let&#8217;s say that you want to display a page with the posts&#8217; titles, dates, and a 200 word excerpt of the post content. This is easy to do with indexes! When you go to create your index of post titles and dates, simply put another field in your index called _description_ with the post&#8217;s excerpt. Now when you go to create the page, you don&#8217;t have to create the excerpt every time, you can simply output what is in your index.

Long story short, use indexes to create lists of data that are specific to what you need. By keeping lists that you already have the grunt work (shortening, searching, etc) completed, you only have to do that work once and be done with it.

(Got data that changes? I&#8217;ll be following this post up with a article on invalidating your caches. Stay tuned!)