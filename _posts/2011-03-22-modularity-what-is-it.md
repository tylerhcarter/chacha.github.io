---
id: 1857
title: 'Modularity: What is it?'
date: 2011-03-22T20:20:48+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1857
permalink: /modularity-what-is-it/
link:
  - 
categories:
  - Programming
---
You may have heard of the term &#8216;Modularity&#8217; before. In fact, I have several articles written about how to use it right on this blog. But, before you can use it you need to know what it is. 

As Wikipedia defines it, Modularity is the concept of taking a complex system, and dividing it up into components that can later be reformed. For instance, if you were making a blogging software you might separate it into, among other things, a RSS Feed Generator and Commenting System. 

Designing a single component to be modular means that the component is able to fit together with the other parts of the system, or even in other similar systems. For instance, if you have multiple projects that require RSS output, you can use the same RSS feed generator in all of them.

**How do I achieve modular code?**

The best way to create modular code is to create each component separately. When you go to build a part, make sure it functions the way you want it to without the rest of your code. And while you are doing this, make sure that it raises errors correctly and acts exactly how you expect it act. Once it is all running, you now have a modular component for your project. After that, you will want to continue on with the other components in your project. Once you&#8217;ve created all the components, and they all work separately, you can begin to bring them together so that they work as a single program. 

**This sounds &#8216;too&#8217; easy.**
  
There are problems with Modular design. The biggest problem with modular design coordination and planning. If you haven&#8217;t done proper planning, different parts can be designed in ways that just don&#8217;t fit together correctly. This is where things like [design constraints](http://chacha102.com/design-constraints-and-planning/), looking at the [big picture](http://chacha102.com/modularity-you-cant-ignore-the-big-picture/), and [proper class planning](http://chacha102.com/code-reuse-and-recycle/) are really helpful.