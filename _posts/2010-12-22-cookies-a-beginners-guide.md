---
id: 1587
title: 'Cookies: A Beginner&#8217;s Guide'
date: 2010-12-22T22:02:52+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1587
permalink: /cookies-a-beginners-guide/
link:
  - 
categories:
  - Programming
---
Cookies are a marvelous feature given to browsers to allow websites to track users from page to page. They have been used for both good and evil during the short lifespan of the Internet, and here I am to provide yet another look on exactly what cookies are, how they are evil, and how they are a necessary evil.

**What are Cookies?**
  
Cookies are similar to a text file. When a website wants to create a cookie on your browser, the website sends over data to the browser, that the browser then stores and makes available to the website whenever you visit it again. The website can store any data it wants (to a certain size limit), and only that website will ever have access to that data (ideally).

**Why are Cookies Evil?**
  
If you are obsessed about your privacy, cookies are one part of the Internet that is out to get you. Websites can use cookies to keep data on how you use their website, how often you&#8217;ve visited, etc. Once you have a cookie on your system, everything you do on that website with that cookie can be tied to you, and thus the website can learn about you and make decisions based on what it knows.

**_That was really disturbing. Could you explain more?_**
  
I might have come off a little strong on the Cookies are Evil thing. However, it is possible for them to do all those things. But, there are certain restrictions on what they can do and there are ways you can stop them. The first thing you should know though is how most of these systems work. Here is a brief explanation:

When you go to browse a website that wants to track you, the website will see if the browser has any cookies from your previous visits to the site. If you haven&#8217;t visited this site before, the website will think you are a new user. The first thing the website will do is create a random number. This is the number that will identify you whenever you access the website. The website will tell the browser to store a cookie with this number inside it. Whenever you visit the website again, this number will be sent to the website. However, on its own this number means nothing. The real magic happens in the database of the website.

Every time you do something the website wants to track, it will create a record in its database with the action you took (viewing a product) and the ID that it previously gave you. Once the website has anywhere from 10 &#8211; 80 of these records, it can begin to try to learn about who you are. (Not your name or address, but things like your interests and what you&#8217;d be willing to buy) The next time you load a webpage, it might go and grab all the records on you and put a banner on the top of the page suggesting a product you might want to buy.

Before you get too alarmed, I&#8217;d like to advocate for all the good guys out there. Lots of websites don&#8217;t do anything like this and simply use cookies to do things like keeping you logged in or allowing you to buy things via a shopping cart. Even doing all the things I&#8217;ve mentioned doesn&#8217;t necessarily mean they should be banished to the depth of hell. If their tracking gives you a better experience, the lack of privacy might be worth it.

**That&#8217;s interesting. How do I stop them?**
  
If you really want to stop someone from track you, you have a few options:

Most modern browser have a button that will clear all cookies. This means that the next time you visit a site, the ID it has given you won&#8217;t be there anymore and it will believe you are a new user. You still will be tracked, but the amount of data they can accumulate on you is limited based on how often you clear your cookies. Some browsers even allow you to clear your cookies every time you close your web browser.

You can also turn off cookies for individual sites. Firefox and Chrome both have options to disallow certain sites from setting cookies on your browser. This is useful for people who have a few sites they want to block. You can also do it the opposite way by disabling cookies for all websites, and then selectively allowing the ones you trust. These will work by simply not sending any cookies set by a website back to them. (You&#8217;ll read more about how cookies work on a browser level in Part 2)

Finally, there are various extensions that will prompt you when a website wants to set a cookie. This is similar to the above option and can be just as effective.

**You said they have restrictions. What are those restrictions**
  
Cookies can only be accessed on the domain they were set on. Meaning google.com can&#8217;t read cookies set by chacha102.com or vice-versa. This ensures that the data created by one site cannot be modified or read by another site. This prevent session hijacking among other security issues.

Cookies can be set to be HTTPS only, meaning that those cookies will only ever be sent to the server if you are connecting via HTTPS. This makes sure the contents of the cookie isn&#8217;t sent over unsecured.

If you want a more in-depth look about how Cookie function, check out [Cookies: What they are and How they work.](http://chacha102.com/cookies-what-they-are-how-they-work-part-1/)