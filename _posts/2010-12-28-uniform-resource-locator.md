---
id: 1598
title: 'URL: The Uniform Resource Locator'
date: 2010-12-28T10:24:05+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1598
permalink: /uniform-resource-locator/
link:
  - 
categories:
  - Programming
---
The basis of the entire internet might be connected to a single concept: The URL. Every website you go to, every link you click on, and every file you download relies on it. The funny thing is that most people don&#8217;t know a lot about how this jumble of slashes and dots works. Well, here&#8217;s how:

**What is a URL made up of?**
  
A URL is made up of several parts that each give specific information about how your web browser (or any other application) should try to connect to a server. A URL is made up the following parts:
  
`The basis of the entire internet might be connected to a single concept: The URL. Every website you go to, every link you click on, and every file you download relies on it. The funny thing is that most people don&#8217;t know a lot about how this jumble of slashes and dots works. Well, here&#8217;s how:

**What is a URL made up of?**
  
A URL is made up of several parts that each give specific information about how your web browser (or any other application) should try to connect to a server. A URL is made up the following parts:
  
` 

As you can see, there are a lot of parts to a URL. But what does each individual part mean?

  * **Scheme**: This is the protocol to use to open this URL. While browsing the web, this is either http or https. However, there are other protocols out there generally used for specific application. Git, a code repository, uses the git scheme to transfer data back and forth.
  * **Username/Password**: Sometimes you might need to send a username and password to a server to access specific files/resources. On most websites you do this through a login system, but non-website based services might require you to give your credentials in the URL.
  * **Domain/IP Address**: The domain/IP address that you wish to connect to.
  * **Port Number**: This is the port number that you wish to connect to on the server. For instance, google.com:5400 will connect to port 5400 on Google&#8217;s server. For web browsing, the standard ports are 80 (http) and 443 (https).
  * **Path/Filename**: This is the path to the specific file on the server you want to access. For instance, example.com/test.html will open test.html.
  * **Query String**: The query string is a series of variables that can pass information to the server. They use the syntax variableName=value&var2=val2.
  * **Fragment**: The fragment tells the browser what part of the page you want to access. The fragment doesn&#8217;t ever get sent to the server, however it is used to automatically scroll to a specific position on a page.

In a relatively small space, URLs are able to convey a lot of information to a server about what it wants to access. Some quick tips to keep in mind while using URLs:

**Always Encode URLs**
  
When you go to output a URL via PHP or another programming language, you should always encode them in a way that won&#8217;t mess up the document you are outputting them in. 

For instance, if you are creating a HTML page and your URL has a &#8216;<' or a '&' in it, HTML is going to thing that those characters are meant to be HTML and not simply text. If you have a URL like: `http://example.com?text=5+is+<+2`

HTML will see the &#8216;<' and think everything after it is the opening of an HTML tag. This can be avoided by writing > instead. The same thing happens with the &. & is used to create HTML entities (like >), and because & is used to delimit variables in the query string of a URL, your URL could be misinterpreted. **When possible, use a full URL**
  
Many people shortcut writing out full URLs by making code like:

<pre>&lt;a href="my/directory"&gt;Link&lt;/a&gt;</pre>

If you are on the homepage, this link would go to http://example.com/my/directory. However, what if this is your main navigation that you use on every page. When you get to http://example.com/hello/world and click on this link, you&#8217;ll go to http://example.com/hello/world/my/directory. This probably isn&#8217;t what you are looking for.

Instead, always use a full URL when linking to items:

<pre>&lt;a href="http://example.com/my/directory"&gt;Link&lt;/a&gt;</pre>

If you are making a website accessed from multiple domains, you can get rid of the domain, but always start from the root directory. (That means that the URL will always start with a &#8216;/&#8217;.)

<pre>&lt;&lt;/code>a href="/my/directory"&gt;Link&lt;/a&gt;</pre>

(As I accumulate more tips on using URLs, I&#8217;ll updated this page)