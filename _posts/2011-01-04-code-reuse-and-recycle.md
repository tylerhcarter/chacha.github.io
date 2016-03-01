---
id: 1648
title: 'Code: Reuse and Recycle.'
date: 2011-01-04T11:17:14+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1648
permalink: /code-reuse-and-recycle/
link:
  - 
categories:
  - Programming
tags:
  - code
  - reuse
---
Have you ever gotten the feeling that you&#8217;re currently writing a piece of code you&#8217;ve written before? I have. And when I started having those feelings too often, I knew that something had to be done. If I spend hours a day writing code for a project, finish the project, and turn around and start writing the same code for another project, we&#8217;ve ran into a major problem. Instead of creating new code that do new, interesting things, I&#8217;m writing code that does the the same, uninteresting things. It is time for a change, for both of us. It is time to write reusable code that can go from project to project with little effort, and can stop us from spending all of our time writing the same stuff.

**Step 1: Plan It**
  
The code you are about to build should be able to last untouched for a long time. Therefore, you need to spend some time figuring out all the details and all the different things this code might run into along the way. For an example, I&#8217;m going to be building a simple class that allows me to connect to a MySQL server using the built-in PHP commands.

I&#8217;m going to start out with a list of things the program has to do:

<pre>1. Connect to a MySQL Server using a Username, Password, and Host field
 2. Select a database
 3. Run a query and return the results
 4. Escape values to prevent query injection
 5. Handle errors using PHP's built-in exceptions
</pre>

This is a simply list, and should be fairly easy to accomplish. One piece of advice when writing code is that it should be very specific to the task at hand. If you need to be able to turn an RSS feed into a PHP object, don&#8217;t let other features creep in like inserting that data into a database. Your code should have a very specific task so it is easier for you to use down the road.

**Step 2: Pusedo Code It**
  
Now that you have a plan, you should start turning this into code. However, programming all the minute details into the program isn&#8217;t what we want right now. We don&#8217;t want to actually commit ourselves to code just yet, instead we want to create a high level design that can easily be manipulated without a lot of extra work. 

Pusedo coding is the practice of writing out the programs flow without actually coding anything. Most of the time it include writing the functions a class has and then commenting about what those classes will do. Here is my example:

<pre>class MySQL{
        private $connection = false;
    
        /*
             Connects to the MySQL Server using the host, username and password.
             Stores the connection created in $connection
        */
        public function __construct($host, $username, $password){
        }

        /*
              Selects a database on the MySQL Server
              Throws an exception if the database does not exist
        */
        public function select_db($database_name){
        }

        /*
              Queries the database and returns the result
         */
        public function query($string){
        }
    }
</pre>

As you can see, my class outlines what each function will do. Now I am coming closer to a finished product and can see what the class with end up looking like. However, it is very easy for me to add, change, or delete functions without wasting any code that they might have contained. 

_Side Tip:_ At this point it would be a very good idea to make sure that your class lines up with your original specifications. If there are certain things in your specifications that never made it into the class, you should add those now. 

**Step 3: Reduce**
  
Some say that simplicity is key to good design. Generally the less code that you use in your class, the fewer bugs you will create. Look at the flow of the class. How does the class get from the initial function call to the result? Are there ways to reduce the amount of code that it takes to get from Point A to Point B.

This is a great place to look at reusing code inside the actual class. If you have 3 or 4 functions that all do similar things (like sorting an array, or validating data), it might be a good idea to make that step its own function. 

**Step 4: Code**
  
This is the part everyone knows about. Now that you&#8217;ve planned out your class, you are able to write code with more certainty that you won&#8217;t need to change it later on. Some of you might ask, what does any of this have to do with reusable code? Well, reusable code is generally code that has been planned out well. If design your classes beforehand and don&#8217;t try to hack it together, you&#8217;re more likely to design a class that will work in multiple situations. 

If you really want some tips on making classes more reusable, here are a few:

  * **Reduce dependencies on other classes.**
  
    If your arguments require that the variables passed in are of a certain class type, it means that every time you want to use this class you also have to use those other classes. I&#8217;m by no means saying \*\*not\*\* to make your code depend on other classes, but do try to make the number of classes you depend upon a fairly small number. If it is absolutely necessary that you 2 or more dependency classes (making your total number of classes 3 or more), you might want to think about packaging less important classes together to make it easier to transport between projects.

  * **Make use of your framework**
  
    If you work in a framework like Java or PHP which already has lots of classes and functions, use them to your advantage. Instead of creating your own Exception classes, use the standard ones given to you by the framework. That way you can assure that anything you do can be ported between projects because they all will most likely be running with those standard classes available.

  * **Be courteous of namespaces**
  
    If you create a class called &#8216;Main&#8217; or &#8216;System&#8217;, chances are that when you go to bring this class into another project, there might already be a class with that name. You should make your class&#8217;s names specific and fairly uncommon. Making a XMLParser is better than making a Parser, however making a XML2OBJParser is even better. (Even though the name doesn&#8217;t roll off the tounge&#8230;)