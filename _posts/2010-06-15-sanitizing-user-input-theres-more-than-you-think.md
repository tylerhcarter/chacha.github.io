---
id: 1006
title: 'Sanitizing User Input: There&#8217;s More than You Think'
date: 2010-06-15T11:25:18+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1006
permalink: /sanitizing-user-input-theres-more-than-you-think/
categories:
  - Programming
---
Thousands of websites are constantly under attack by hackers and other malicious users. There are groups on the internet specifically devoted to causing havoc and others who simply want to see what they can get away with. One of the first line&#8217;s of defense you can instill into your program to protect against these types of users is to properly sanitize user input. However, before we can talk about how to sanitize user input, we must first find out what it is.

**What is User Input?
  
<span style="font-weight: normal;">The definition of user input that we will use is anything that can is sent to the server via  user. These values can contain all sorts of things and should be sanitized to make sure that it only contains what you want.</span>** 

**<span style="font-weight: normal;">While some user input might be easy to spot, you should be aware of all the different ways users can get data into your system. The first, and most obvious one is through form fields. You are asking a user to type data into your form, and then submitting it. </span>** The submitted data should always be checked for bad data, and this bad data should be removed. We&#8217;ll talk about removing bad data in a minute.

There are also other types of user input. Cookies, for instance, are user input. While it takes a technically-savy user to change the values, it is very possible to change, create and delete cookies on any machine. Another common form of user input is URL parameters. For those who aren&#8217;t sure what URL parameters are, they are the key-value pairs found in a URL after the question mark. In the following URL, the key value parameter &#8220;key1=value&#8221; is user input: &#8220;http://example.com/?key1=value&#8221;.

Finally, headers are user input. Headers such as HTTP_REFERER and others are able to be spoofed by the client, which can end up impacting your service.

**So, how do I sanitize it?
  
<span style="font-weight: normal;">So, now that we know what we can&#8217;t trust, how do we use it in a way that is reliable? Most of today&#8217;s languages comes with a multitude of modern ways to make sanitize data. However, you should know what each method does, and when the use them.</span>**

_Escaping
  
<span style="font-style: normal;">One method of sanitization is called escaping. Escaping takes characters that have special meanings in a language, and tell the compiler to remove the special meaning. This is most common when you are entering data into a database, such as MySQL. While I won&#8217;t go too much into escaping, the part you need to know is that data being entered into a database should be escaped properly. You&#8217;ll want to do some Google research to find your proper escaping mechanism. (You can even read the database&#8217;s manual to create your own)</span>_

_Stripping
  
_ Another common form of sanitization is stripping. This is when you remove specific letters or sets of letters completely from the string. Suppose that you wanted a user to enter a username. You might want to strip out all characters that are not either letters or numbers.

A widely used practice for websites is HTML tag stripping. This type of stripping identifies HTML tags inside of a string and removes them. This ensures that when you go to display that data, it can&#8217;t be used to change the HTML structure of your page.

_Converting
  
<span style="font-style: normal;">Converting dangerous characters into non-dangerous characters is also very useful. Instead of stripping HTML tags from a string, you could convert all of the brackets characters into their html entities so they display as angle brackets on the page, but aren&#8217;t treated as actual HTML.</span>_

_Restricting
  
<span style="font-style: normal;">The final form of sanitization I&#8217;ll talk about is restricting the number of values to a predefined group. Let&#8217;s say you have a field that your user can enter a 2 letter state abbreviation. To sanitize this, you can define a list of state abbreviations in your code, and check if what the user entered is in that list. If it isn&#8217;t, you can reject the value and tell your user that this is invalid data. (While this is a method of validation, it can also be considered sanitization)</span>_ 

**Validation and Sanitization are not the same.
  
<span style="font-weight: normal;">Validation and Sanitization are very different. Validation is making sure that the data you have is correct. Sanitization is making sure that the data you have doesn&#8217;t contain anything that could cause damage to your program. Knowing how to use each of them is crucial in making a reliable and safe web application.</span>**