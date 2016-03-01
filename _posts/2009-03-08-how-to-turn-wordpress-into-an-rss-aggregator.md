---
id: 608
title: How to turn WordPress into an RSS Aggregator
date: 2009-03-08T07:31:33+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=608
permalink: /how-to-turn-wordpress-into-an-rss-aggregator/
wp_jd_clig:
  - http://cli.gs/4tErT5
  - http://cli.gs/4tErT5
jd_tweet_this:
  - yes
  - yes
categories:
  - Misc
---
 

I am currently on of the administrators of <a href="http://thenextintech.com/" target="_blank">NextTech’s</a> servers. (NextTech is a group of young bloggers who collaborate together on tech news.) Over the past 2 weeks, we have been putting together the back bones of our system, including self-hosted WordPress blogs, Feedburner feeds, Ad management, and etc. One thing we wanted to do from the beginning is to aggregate all of our content into one place, that people could skim over a large amount of content. Once they found something they liked, they could simply click and go. <!--more-->

So, in essence, we were trying to build a Techmeme for our content. We wanted to grab all of our items via RSS, put them on a single page with descriptions, and link back to our page. All of this should happen automatically, and we need it to look good. That is when I started working on my own, homebrewed solution. I know PHP and MySQL, so I set to build one. The set up turned out to work really well, except for small things like character encoding, and more importantly, dealing with different types of feeds.

We scratched the idea of doing a homebrew solution, and I set to build a WordPress version of this aggregation. Here I am to share it with you.

**What will you need?**

  * A Self-Hosted WordPress Blog (Duh) 
  * WP O Matic

Pretty short list. Basically, what WP O Matic allows you to do is to post things that are grabbed from RSS. You can simply plug in the rss feed, set the category you want it to go to, and possibly other options, and run it. It even allows for support of Cron tasks so that you can have the listing updated when no one is visiting your site.

It is really that simple. Now all you have to do is plug in a blog theme that uses excerpts of the post instead of the full post, and on every feed, check the box that says ‘Link to source’. This will make sure that when people click from the front page, it will go to the actual blog post, instead of the one hosted on your server.

I hope to post more of these quick WordPress tips as I learn stuff from managing NextTech servers. Hope you will check out the rest of our content at <a href="http://thenextintech.com/" target="_blank">TheNextInTech.com</a>