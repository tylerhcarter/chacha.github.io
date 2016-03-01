---
id: 1569
title: 'Cookies: What they are, How they work'
date: 2010-12-22T15:39:10+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1569
permalink: /cookies-what-they-are-how-they-work-part-1/
link:
  - 
categories:
  - Programming
tags:
  - browser
  - cookies
  - internet
---
Cookies are a marvelous feature given to browsers to allow websites to track users from page to page. They have been used for both good and evil during the short lifespan of the Internet, and here I am to provide yet another look on exactly what cookies are, how they are evil, and how they are a necessary evil.

**What are Cookies?**
  
Cookies are pieces of text. When a server tells a browser that it wants to store a cookie, it gives the browser a string of text and whenever the browser returns to that website, it sends that text back to the server. Along with the contents of a cookie, the browser stores:

  * Name
  
    A website can have multiple cookies, and the easiest way to organize these is to give each cookie a name.
  * Expiration
  
    When the cookie will expire. As you might imagine, once a cookie expires it is deleted.
  * Domain
  
    The domain that the cookie is tied to. Browsers are smart and only allow a website access to cookies from its domain.
  * Path
  
    The path of the website that can access the cookie. If its value is /test/, only files inside that directory (or in subdirectories) can access that cookie.
  * HTTPS
  
    If a cookie is HTTPS-only, the website won&#8217;t be able to access it when you are using HTTP.

Many of these options keep cookies from being tampered with. By restricting both domain and path access to a cookie, you can tell the web browser exactly where the cookie needs to be used and can protect it from code running on any other part of the server. Furthermore, marking a cookie as HTTPS-only ensures that the only time a cookie will ever be sent to the server is over a secure connection, preventing things like [Session Hijacking](http://en.wikipedia.org/wiki/Session_hijacking).

Now that we know what cookies are, we are going to turn our head towards how they function. And to know about that, we have to know about Headers.

Headers are meta-data that gets sent to your browser before a page is loaded, and when that page is returned. It contains information about what browser you are using, what page you are requesting, and more. A typical set of headers for requesting google.com would look like: 

`Host: www.google.com<br />
Accept-Language:en-US,en;q=0.8<br />
User-Agent:Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/534.15 (KHTML, like Gecko) Chrome/10.0.612.3 Safari/534.15`

Cookies are just another set of headers. When I visit a website, my browser looks at all the cookies on my machine and based on the domain and path restrictions, makes a list of all the cookies that should be sent to the website. It then creates a header called &#8220;Cookie&#8221; with all of the cookies delimited by semi-colons, and sends it to the server. Something like:

`Cookie: rememberme=true; user=12345; views=5010`

Just for a reference, the format is cookie\_name=cookie\_value. 

It works almost the same in reverse. When you request a webpage, the server will send a set of header back to your computer telling about the webpage such as the size of the webpage, the language, and other information that the browser needs to know. To set a cookie, the website simply sends a Set-Cookie header with the data it wants to be saved:

`Set-Cookie: cookie_name=cookie_value; expires=Fri, 21-Dec-2012 22:25:57 GMT; path=/; domain=.domain.com`

In this case, semi-colons separate sets of parameters. The first set of data is the actual cookie. After that is the expiration time, the path restrictions , and what domain it belongs to.