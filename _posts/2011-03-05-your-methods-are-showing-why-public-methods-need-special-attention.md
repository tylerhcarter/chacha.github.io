---
id: 1825
title: 'Your Methods Are Showing: Why Public Methods Need Special Attention'
date: 2011-03-05T10:54:58+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1825
permalink: /your-methods-are-showing-why-public-methods-need-special-attention/
link:
  - 
categories:
  - Programming
tags:
  - design
  - interface
  - methods
---
So you are about to create a new class. You go to define the first method. You mull over whether to make it a private or public method, choose public, and go on with your day. This isn&#8217;t exactly the best way to create a class, especially one that you might want to use for other projects or even distribute to other developers. 

The fact is, the methods that you declare public in your class are special. They are the methods that code outside of your class can interact with. This is both good and bad. It is good because without these methods, outside code can&#8217;t tell your class to preform its function or obtain the product of its work. It is bad because when outside code interacts with these methods, pretty much anything can be passed in as an argument and any method can be called at any time in any order.

Because of this, you need to have a basic checklist of defenses set up to make sure the public methods of your class can withstand whatever some other chunk of code throws at it.

**1) Set Data Expectations and Check Them**
  
You should have expectations for any data coming in from outside classes. Checking that the data they give you is a certain datatype (string, integer, object, etc) should happen as soon as possible. If the data given doesn&#8217;t meet expectations, you need to present them with an error.

By checking the data as soon as it comes into the class, it is easier to debug what is going wrong later on. It also means that you don&#8217;t have to follow your class&#8217;s logic to figure out if a piece of data is actually checked.

**2) Make sure your object is in the correct state**
  
For some objects, you might be expecting certain conditions to be met before a specific method is called. For instance, a disconnect method would expect connect to already be called. You need to check the state of your object to make sure you are in a state where you can preform your task. For instance, you would check that there is a connection already opened before trying to disconnect it. If there isn&#8217;t a connection you could create an error, or you could decide that the function has technically done its job (ensure that there isn&#8217;t a connection open).

**3) Standardize your return values**
  
Because your class might have a lot of public methods that return data (think a class representing a database table), you need to make it easy for others to figure out what data you are returning. Because of this, similar methods should return similar data. If your getPosts method returns an array, getComments should also return an array. These arrays should also use similar field names with a similar naming convention (camelCase, etc).

_Tip:_ The reason all of these things should be standardized is for consistency. If you are consistent with return values, method names, etc, other developers know what to expect which makes your class more useful. 

_Tip_: When you create a method that returns an array, it should _always_ return an array. Even in dynamically typed languages like PHP, an error should not mean you return false but instead return an empty array. If you&#8217;d like, you can raise an exception, but never return a boolean when developers expect an array.