---
id: 1013
title: Don’t Cross the Beams! Why Object-Based Database Connections Rock
date: 2010-06-18T08:00:44+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1013
permalink: /dont-cross-the-beams-why-object-based-database-connections-rock/
categories:
  - Programming
tags:
  - databases
  - object oriented programming
  - programming
---
You can pretty much guarantee that any dynamic website is going to, at some point in time, connect to a database. It is a good idea to have a bit of knowledge about how your particular language works with different databases, and what tools are at your disposal. If you&#8217;ve worked with databases in PHP for any length of time, you&#8217;ve probably came across the MySQL library. Functions like mysql\_connect() and mysql\_query() are extremely common. However, you can save yourself a lot of time by not using them.

Now, before you explode on me, let me explain my reasoning. Every time you have to type out the words mysql_query() you might be wasting your time. This is because if you ever have to switch databases, involve multiple servers, or have any other weird database configurations brought to your code, you are required to go back and change all of those commands you just typed. Let&#8217;s take this example:

<pre>mysql_connect(); // A mysql_connect() call with no parameters uses php.ini's default settings.
$result = mysql_query("SELECT * FROM table");</pre>

This seems like a very simple command. It connects to the database, and makes a query. And for very small sites, this may be the perfect solution. However, if you code everyday like this you could be setting yourself up for a lot of work. Let&#8217;s say your boss calls and tells you that you have to grab data from another server. That shouldn&#8217;t be too hard. We can just modify our script to grab data from the new server.

<pre>mysql_connect();
$result = mysql_query("SELECT * FROM table");

mysql_connect("differenthost.com", "differentuser", "differentpass");
$result2 = mysql_query("SELECT * FROM table2");</pre>

Now we have made multiple connections and have gotten data from each server. But what if this was more complicated? What if you had to make a query to Server A, use that to make a query on Server B, and then make a third query on Server A. You could try messing around with link identifiers, but that is going to get messy:

<pre>$server1 = mysql_connect();
$result = mysql_query("SELECT * FROM table", $server1);

$server2 = mysql_connect("differenthost.com", "differentuser", "differentpass");
$result2 = mysql_query("SELECT * FROM table2", $server2);

$result3 = mysql_query("SELECT * FROM table 3", $server1);</pre>

Well, that isn&#8217;t too bad. But what if Server A suddenly switches to a Non-MySQL protocol? You&#8217;re going to have to go back and rework all of your logic, and this is only on a 7 line script. If you&#8217;re dealing with thousands and thousands of lines of code, managing servers is going to be hard unless you are using a proper object to control how the queries get sent.

With objects, you can create an object, assign it to a variable, and then anyone who wants to make a query can simply call the query() method on that object. It doesn&#8217;t matter what server is being queried on, it doesn&#8217;t care what type of server it is, or anything else for that matter. As long as you return an array with the results they want, it will work. This also means that when you change how a database is accessed, you only have to change it in one place.

Let&#8217;s first define what a Database Connection object should look like:

<pre>abstract class DatabaseConnection{

	abstract public function connect($host, $user, $pass);
	abstract public function disconnect();
	abstract public function query($queryString);	

}</pre>

Right now, this object is _abstract_, which means that what the functions actually do have not been defined. We&#8217;ve simply defined what functions must be available, and what arguments they need to accept. For this DatabaseConnection, we&#8217;ve made it simple. A connection simply needs a way to connect, disconnect, and make a query.

Let&#8217;s make one in MySQL:

<pre>class MySQLConnection{

	public function connect($host, $user, $pass)
	{
		$this-&gt;connection = mysql_connect($host, $user, $pass);
	}

	public function disconnect()
	{
		mysql_close($this-&gt;connection);
	}

	public function query($queryString)
	{
		return mysql_query($queryString, $this-&gt;connection);
	}

}</pre>

As you can see, this is a very simple connection. And you can call it like this:

<pre>$db = new MySQLConnection;
$db-&gt;connect("host", "user", "pass");
$db-&gt;query("SELECT * FROM table");</pre>

But this isn&#8217;t the fun part. Let&#8217;s say we have the above code with the multiple databases, but used objects instead:

<pre>$db = new MySQLConnection;
$db-&gt;connect("host", "user", "pass");
$db-&gt;query("SELECT * FROM table");

$db2 = new MySQLConnection;
$db2-&gt;connect("host2", "user2", "pass2");
$db2-&gt;query("SELECT * FROM table");

$db-&gt;query("SELECT * FROM table");</pre>

Now, let&#8217;s say we wanted to use a different type of database. Instead of having to change a bunch of code, we change one line and nothing else:

<pre>$db = new PDOConnection;
$db-&gt;connect("host", "user", "pass");
$db-&gt;query("SELECT * FROM table");

$db2 = new MySQLConnection;
$db2-&gt;connect("host2", "user2", "pass2");
$db2-&gt;query("SELECT * FROM table");

$db-&gt;query("SELECT * FROM table");</pre>

Now, wasn&#8217;t that easy? And in large projects, this saves hours and hours of time because you only have to change a couple lines to make a change. Using the old-fashion way, you&#8217;d have to change each line that called mysql_query(), and get its PDO equivalent.

Try it out. Use an object based database connection on your next project. Not only will it save you time, it gives you a ton more flexibility in how you connect to your database.