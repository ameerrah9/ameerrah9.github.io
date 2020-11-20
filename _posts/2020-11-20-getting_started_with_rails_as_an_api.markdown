---
layout: post
title:      "Getting Started with Rails as an API"
date:       2020-11-20 23:33:56 +0000
permalink:  getting_started_with_rails_as_an_api
---

An API is known in the programming world as an Application Program Interface. What does this mean you ask? Well from my understand an API is used to grab data from a particular source, usually a database.

You may ask, what is a database? From my understanding a database is used to store and retrieve information, and when I get really good at communicating with these suckers, I'll become a better engineer.

An API can be created by anyone, that's the really cool part. The way to get started will be explained in this blog post. Now the first thing I will tell you is, APIs enable programmers like me, to access and display on a web page.

APIs can become the grit of your application because of the freedom and the ability to grab any informational database and use it like a tool. APIs are great because your program is allowed to be multi-resourced. It has range, it has freedom, go create. This tool comes with flexibility by using a powerful gem called the Fast JSON API. The Fast JSON API gem provides a quick way to generate and customize JSON serializers. 

Woah slow down! What are you even saying?
Okay, I'll break it down, you're probably asking, "what is JSON?" It stands for JavaScript Object Notation. JSON (JavaScript_Object_Notation)  is a simple data format that uses sets of the familar *key & value pairs* to store information. Back to that information storing thing again. JSON is chosen because it uses javascript to pass information around. Serializers enable us to handle the logic of arranging our JSON data the way we want it.

There are many gems out there, but there is a particular gem in Rials that I truly have fallen madly in love with. It was instant connection, didn't make much for me to realize the power of this tool. It's not just me that can confirm how brilliant it is. Using this popular option, the Fast JSON API gem creates a JSON serializer for Rails APIs. It provides a way for us to generate serializer classes for each resource object in our API that is involved in customized JSON rendering.

Setting up Fast JSON API
To add the Fast JSON API gem to your Rails program, go to your project's Gemfile and copy and paste this line there:

```ruby

gem 'fast_jsonapi'

```

Then run bundle install in your terminal.

Once installed, you will gain access to a new generator, serializer.

Godly Gem!



