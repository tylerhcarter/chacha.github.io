---
id: 2016
title: Using Factories
date: 2012-01-18T16:23:48+00:00
author: Tyler (Chacha)
layout: post
guid: http://chacha102.com/?p=2016
permalink: /using-factories/
link:
  - 
categories:
  - Programming
---
Factories are neat, because they allow you to set common properties for objects before you create the object. Plus, all the objects coming out of the factory will have those same settings.

For instance, take the follow factory:

    
    class Item{
        public $price = 0;
    }
    
    class ItemFactoryA{
    
        public $item_price = 15;
        public function get(){
            $item = new Item;
            $item->price = $this->item_price;
        }
    
    }
    
    $iFactory = new ItemFactoryA;
    $item = $iFactory->get();
    

The benefit of this is that every item coming out of FactoryA will have the same price. This is useful if you are going to set the price once, but want to remember it for a while.

In a real life scenario, it could look more like this:

    
    class UTC_TimeClock{
        public function get_time(){
            return time();
        }
    }
    class TimeZoneClock{
        public function __construct( $utc_clock, $timezone_offset ){
            $this->utc_clock = $utc_clock;
            $this->timezone_offset = $timezone_offset;
        }
        public function get_time(){
            return $this->utc_clock->get_time() + $timezone_offset;
        }
    }
    class TimeZoneClockFactory(){
        private $utc_clock;
        public function __construct(){
            $this->utc_clock = new UTC_TimeClock;
        }
        public function build( $timezone_offset ){
            return new TimeZoneClock( $this->utc_clock, $timezone_offset );
        }
    }
    

This factory would make sure that all of the Time Zone clocks are running off of the same UTC time clock, but that they all could have different offsets based on what time zone they are representing. 

There are many more examples of how this could be useful.