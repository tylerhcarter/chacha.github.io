---
id: 987
title: Minimizing your outage when switching hosts.
date: 2010-06-09T04:27:14+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=987
permalink: /minimizing-your-outage-when-switching-hosts/
categories:
  - Programming
---
Every website owner or maintainer will have a point in time when they have to switch where their website is located in terms of physical storage and/or web host. What can you do to minimize the down time? I, like many others, have had experience switching services. This blog, in fact, was just recently moved.

I made the decision to switch all of my content from my old server hosted at MediaTemple, to my new server hosted at Pair Networks (PairLite to be exact). Not only did I get more overall (Ruby, Python, etc for no extra charge), I also got a more granular control over my DNS and site settings. These features are crucial for me because I love to tinker around with languages, which I just couldn&#8217;t do on MediaTemple without paying extra. Plus, I&#8217;ve used Pair before and have heard some excellent things about it. But enough about that.

There are a few items you should know about when switching:

**DNS Settings**

The slowest part of the internet is probably its address book. DNS stands for **domain name system**, and it is what connects you to your favorite web sites everyday.

If you haven&#8217;t had experience with DNS, here is a brief explanation. The internet is made up of numbers. Each computer connected to the internet is given a number to identify it in the form of an IP address. If it weren&#8217;t for humans, computers could connect with each other without ever having to type in a single _.com_ or _.net_, they would simply use IP addresses to get around. However, for us humans, the makers of the internet have came up with a system that translates domain names: _chacha102.com_, into IP addresses: _72.130.131.100_. Whenever you type in example.com, your computer goes up to a global address book, gets the number that matches with the domain address, and then connects to that computer to get your web page. Wikipedia has an [excellent article](http://en.wikipedia.org/wiki/Domain_Name_System) on this if you are interested in it further.

So, how does DNS make our switch slower?

Whenever your computer goes to find out that _example.com_ is really _12.34.57.78_, it stores it for 24 hours so it doesn&#8217;t have to look it up again. This makes our browser faster, especially when we are going between pages on the same website, because our computer doesn&#8217;t have to go to the address book for every single page. However, this caching effect doesn&#8217;t help us when we _want_ the browser to look up the IP address again. Any browser that has looked up the address in the past 24 hours won&#8217;t look it up again until that 24 hours expires. This means that when we tell the global address book that chacha102.com is no longer at 12.34.56.78, but instead is at 87.65.43.21, the computers that have that data cached won&#8217;t be updated for a while.

**Physical Storage**

The actual data that runs your website is stored on a server, with an IP address. Everytime a user wants to access your data, it has to make a request to your server, and your server must respond with the data that the user wants. This is how you load web pages. However, unlike DNS, this data is always up-to-date. This means that if you remove files from your server, the user won&#8217;t be able to get to them. This can cause problems when switching hosts, because if you remove the data from your old web server and put it on your new web server, people that are still going to the old web server (people who have the IP address cached), are going to be getting a bunch of blank pages. The other side of this is if you keep all of your data on your old server, and direct people to your new server (planning to transfer the data after 24 hours), you will have everyone who has never visited your site, as well as people who are updating their cache, will get blank pages on your new server.

**How to migrate properly?**

So, we&#8217;ve been presented with this problem. For a 24-48 hour period, users will be going both to your old and new server. How do you make sure that the people going to your old server don&#8217;t believe you have just vanished, and make sure people going to your new server don&#8217;t believe the same thing?

Well, there are a couple solutions:

**Host the data both places**

If you have a blog or something that is fairly static, you can run your blog on both the old and new server, and then just start updating the new server with new content. In about 48 hours, you can go take down the files from the old server and you can be on your merry way. This is probably the easiest solution, as most people won&#8217;t realize you have switched servers.

**Maintenance Pages**

The other option is to place a maintenance page on your old server that says the site is currently down for maintenance. Then, whenever the user&#8217;s DNS cache updates, they will be directed to the new server and it will appear as if the site is back online.

There are more ways to mitigate this change. These are just a few solutions I&#8217;ve found useful to make sure that users both on the old and new server of a transfer don&#8217;t think you&#8217;ve simply vanished. It is a good idea to keep your users in the know, and not just serve them blank pages.