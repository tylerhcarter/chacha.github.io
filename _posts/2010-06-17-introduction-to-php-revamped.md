---
id: 848
title: Introduction to PHP – Revamped
date: 2010-06-17T09:51:59+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=848
permalink: /introduction-to-php-revamped/
aktt_notify_twitter:
  - no
categories:
  - Programming
tags:
  - php
  - programming
---
_This was originally posted several months ago. I have updated it and brought it back as I still believe that PHP is one of the world&#8217;s most used web-based programming languages._

We live in a world dominated by internet, which is being used by hundreds of millions of people everyday, yet most of these people don&#8217;t know much about what it is being ran on. Here I&#8217;ll try to explain where exactly PHP steps in and works its magic. Hopefully this gives you a better understanding of what happens behind the scenes.

**Introduction**

Now, there are many different programming languages you can learn, but I am just going to focus on one of the easiest and most convenient called _PHP_. PHP is a programming language that runs things like Drupal and WordPress, so it will probably also be the most useful to the average user.

**The Internet is a World of Servers.**

Before we get into PHP, lets talk about the Internet. Whenever you want to visit a website, such as http://chacha102.com, your computer connects to a box on the internet. This box is called a &#8216;server&#8217;, and is located somewhere in the world. It looks very much like your computer, and it&#8217;s plugged into the internet the same way your computer is. Whenever a browser wants a page, it tries to finds the server that hosts the website you are looking for, and asks for the page you want, which the server then gives back and your browser shows you.

**PHP: The Middleman**

When your browser connects to the server and asks for a page, PHP steps in. In the old day of servers, files were stored on the server and when you requested the file, the server would just give it to you. In today&#8217;s servers, instead of immediately giving you the file you requested, the web server looks through the file for PHP code. If it finds any PHP code, it processes the code, and sends the resulting page to the user.

Because of this action, PHP is very secure. The PHP code is being processed on the server, before the page is ever sent to the browser. This means that no matter who is connecting to your website, they will all get the same page. Unlike Javascript or other client-side programming languages, PHP doesn&#8217;t require the person connecting to the website to have PHP installed. Instead, all you need to run a PHP-based website is a server that has PHP on it. This also affects some other parts of the web-development process.

**Javascript and PHP**

One of the questions most frequently asked is how to make PHP and Javascript communicate with each other. The problem is many people don&#8217;t know that PHP is server-based (runs before the page is sent to the browser) and Javascript is browser-based (runs once the page is sent to the browser). This means that they cannot communicate back and forth. In order for you to get data from Javascript to PHP, you need to request another page on the server, and give it the data you want to send. (This is called AJAX)

I hope this helps you grasp a better understanding of PHP. As one of the most widely used programming languages out there, it is a good idea to know what it can and can&#8217;t do.