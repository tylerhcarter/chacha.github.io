---
id: 1778
title: 'Modularity: You Can’t Ignore the Big Picture'
date: 2011-03-01T22:11:24+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=1778
permalink: /modularity-you-cant-ignore-the-big-picture/
link:
  - 
categories:
  - Programming
tags:
  - building
  - design
  - first
  - robotics
---
Building modular components can be a very efficient method of construction. Each component is its own mini-project, and all the parts come together to form something greater than the sum of its parts. Instead of building a blog, you build a post writing/editing system, a commenting system, an RSS generator, and afterwards you piece them all together.

As ideal as all of this sounds, there is a trap that you can fall into when you do things modularly. And it has to do with requirements.

At the end of the day, your modular component is a part of a bigger picture. When you&#8217;ve finished building your component, the rest of the project needs to be able to interface with your component to get work done. If you build something that isn&#8217;t easily dropped into the bigger project, you will end up wasting a lot of time.

Whenever you design something modular, you need to list out your requirements. This includes everything from the tasks your component needs to preform to the way it needs to interact with the main project. You also need to be aware of the things your component requires to work, and make sure that those are available when it comes time to pull everything together.

Here are a few quick questions you should ask when you go to design a modular component:

**1. What actions does the main project need to be done?**

While this might sound obvious, it is very important to make a list of the functionality the component is required to provide. This does two things that help everyone&#8217;s productivity and sanity. With a written list of functionality, no one needs to try to add a ton of extra functionality &#8220;just incase&#8221;. Instead, once everything is checked off you can move on to another component. 

It also helps everyone&#8217;s sanity by making a sort of contract that states exactly what the component needs to do. There isn&#8217;t any confusion over what a component should do and not do when there is a list sitting in front of you. And if the main project needs more functionality they can change the contract, but only after making sure everyone creating the component knows about the changes.

**2. Where are the connection points between the main project and my component?**

Knowing the entry points to your component is crucial. All interactions between the main project and your component should be carefully looked at and tested for possible errors. Making sure that your component can handle all of these interactions properly will make integrating it with the rest of the project less painful.

One of the most important tests is data validation. The data that is passed to your project should be validated and verified to make sure it is in the proper format. It is unendingly annoying to be expecting data in one format, and getting errors because the data you are getting was never put into that format.

**3. What are my dependencies?**

Whether you have just a few dependencies, or a lot, listing them and making sure that they will be available in the main project is important. If you use a library like jQuery, make sure that when your code gets merged you will still have access to it. Verify that systems like databases and mail servers will work the way you expect them to, and if possible create code to make it easy to adapt your component to them when they do change.

When you&#8217;ve completed all 3 of these steps, you should have a very good idea of what it will take to integrate your component with the main project. Now all you have to do is build it. Have fun!