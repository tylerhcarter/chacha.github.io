---
id: 1987
title: 'Building a Language: Math Expressions'
date: 2011-05-17T16:27:07+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1987
permalink: /building-a-language-math-expressions/
link:
  - 
categories:
  - Programming
---
If someone tells you to list every math operation you know, you might tell them: addition, subtraction, multiplication and division. And you would be right. Each of these are math operations. But to a programming language, these are the least used math operators in existence.

When a programming language goes to evaluate an expression, it must deal with a variety of math operators. Each of these math operators has a common behavior: it takes 2 values (on the left and on the right) and spits out a single value (the result of the operation). 

Basic arithmetic operators all fit this description. And if you were to write a programming language, you could very easily model those operators after this behavior. However, it would be a big waste to forget 3 other operators that have this very same behavior: equals, and, and or. 

If you think about the &#8216;==&#8217; operator (or equality operator), it takes the value on the left and compares it to the one on the right. If both are equal, it outputs a single value: boolean true. The same can be said for &#8216;and&#8217; and &#8216;or&#8217;. Both look at the values on the left and right of them and output true or false, based on the keyword in use.



If you look at [SomeLanguage](http://github.com/chacha/SomeLanguage), you&#8217;ll see that all of these math operations are implemented using a single [MathOperation](https://github.com/chacha/SomeLanguage/blob/master/src/somelanguage/Interpreter/Expressions/MathOperation.java) behavior that allows [expressions](https://github.com/chacha/SomeLanguage/blob/master/src/somelanguage/Interpreter/Expressions/) to be evaluated very easily.