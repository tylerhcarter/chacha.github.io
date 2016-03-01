---
id: 998
title: 'Globals: What they are, and why not to use them.'
date: 2010-06-12T08:00:23+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=998
permalink: /globals-what-they-are-and-why-not-to-use-them/
link:
  - 
categories:
  - Programming
---
If you&#8217;ve programmed for a while, you&#8217;ve probably heard of the term &#8216;global variables&#8217;. The idea behind global variables is that they are available anywhere in your code, no matter if you are inside a function, class, or any other scope where you wouldn&#8217;t generally have access to variables outside that block.

In PHP, a sample of variable would be:

<pre>Global $global_var;
$global_var = "Hello";
function sayHi(){
    Global $global_var;
    echo $global_var;
}
sayHi();  // echos "Hello"</pre>

The reason this function works without having to pass in $global_var as an argument is because of the global keyword. The global keyword breaks through the barriers generally given to a function (no variables exist except super-globals and arguments), and allows access to this variable. This technique can come in handy a lot of places. WordPress uses it heavily to make the work template designers have to do with WordPress very minimal. But just because WordPress does it, doesn&#8217;t mean that it is a good practice.

**What is so evil about globals?**

Well, simply put, they make your code very unreliable. When you pass a variable into a function through an argument, the function explicitly requires that you supply that argument. By requiring that an argument be passed in, you are telling whoever is trying to call your function that your function won&#8217;t work without that argument present. However, by using globals you aren&#8217;t able to state any of this.

When you use a global, it is very hard for other developers to know what you need. For instance, the above function requires that a variable named $global\_var is set, and it has some sort of value. If neither of these conditions are met, your function won&#8217;t work the way it is intended to. However, because it is never stated in the function parameter list that this function requires information (whatever is held in $global\_var), anyone trying to call your function won&#8217;t know that they need to set $global_var before calling your function.

On the other hand, if you rewrote your function like this:

<pre>function sayHi($text){
    echo $text;
}
$nonglobal_var = "Hello";
sayHi($nonglobal_var);  // echos "Hello"</pre>

Now, the only way to call your function is by providing an argument. If someone doesn&#8217;t provide an argument, PHP will error on them and they will be forced to correct their code.

**But I&#8217;m the only person working on my project, and I know what I need!**

There are many programmers who write code alone, without anyone else needing to understand the code, who feel that it is unnecessary to state the requirements of a function upfront because they already know everything there is to know about the system. However, this is a very dangerous mentality to be had. Sure you might know what your application does now, and what the requirements are now, but will you still remember all of that in 10 years? 20 years? By writing as explicitly as possible, you make sure that no matter how long ago you wrote a piece of code, you are able to understand it and modify it.

Furthermore, you never really know if you will be the only person to ever work on this code. If the project you are working on turns out to be a gigantic hit, and you have to hire other programmers to add features, optimize, and prepare it for millions of users, you are going to have one hell of a time explaining the entire program to your new employees.

**So, what is the take-away?**

The takeaway from this is pretty straightforward. By using globals, you reducing the stability of your program because you don&#8217;t explicitly state what you need for a certain function to run. If you avoid globals, you will make your code more explicit and reliable, and you&#8217;ll be able to read it in 20 years and still know how your system works.

Other Resources: 

  * [How to Write Clean, Testable Code](http://chacha102.com/shares/how-to-write-clean-testable-code/)
  * [Code: Reuse and Recycle](http://chacha102.com/code-reuse-and-recycle/)