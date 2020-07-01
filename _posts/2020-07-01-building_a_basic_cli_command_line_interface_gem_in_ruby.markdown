---
layout: post
title:      "Building a Basic CLI (Command Line Interface) Gem in Ruby"
date:       2020-07-01 16:21:30 +0000
permalink:  building_a_basic_cli_command_line_interface_gem_in_ruby
---


Engineering A Simple Ruby CLI Application

Command Line Interface Project using Last FM Music API

Building a basic CLI Gem

It’s Project Week! Time to work on my first project. The requirements included build a Ruby gem that provides a Command Line Interface (CLI) to an external data source. My creative side really got to shine during this project week. My application's idea needed to utilize a music catalog source such as Spotify. I quicky learned that Spotify's API requires OAuth so I decided on using an external data source that did not have many hassles and utilize an API from a public website, the Last FM API. 

Getting and External Data Source
This one of the first obstacles I faced during my CLI build. Biggest challenges included finding a voable API to use and deciding whether to scrape a website or get the data from an external source using and API. It was the first step to understanding what data I could use and how the flow of my program would work. WIthout knowing the data given from the API it's difficult to structure your application. Luckily the Last FM API has really readable doucmentation so I was able to easily retrieve a Base URL for my different Requests.

Before we begin coding, it's neccessary to create a git repository on Github.

For this project I have decide to access data form Last FM API (BASE_URL = 'http://ws.audioscrobbler.com/2.0/').

CLI File Structure
Before I even include any code in my program I had to set up my file structure in Visual Studio Code. Getting project files well organized was one of the first steps to building a successful CLI. Certain code goes in certain files based on what the code does. First step was running bundle install to grab all of my dependencies. In the root directory of a Ruby application, you usually see a basic folder structure. The top folders within my project includes: bin, lib, config, and spec.

My bin file is where my program actual gets ran. The bin folder is where my executables and libraries are stored. The bin file is important because it's here that I call upon the various files to initiate the application. The bin contains the musiqdex file which tells the application which file to run in which order.

Classes
Each one of the ruby files, denoted with a .rb, houses a single class and its accompanying methods. That single class is responsible for one single part of the application. For example, the top_songs.rb file contains the class called Songs, which is responsible for creating song instances.

The App Build
I have designed to build this app to access different songs based on keyword and return the list of songs in list form. I thought it would be interesting and useful to build a gem that searches some specific of these songs and display back a list and also give a brief detail (song title, artist, listeners) about them. The user is welcomed with a message and prompted to choose a keyword.

Choose a keyword
A list of top 30 songs will display with keyword included in each song title. The user is then prompted to choose a song from a numbered list that they want more information on. Once a song is chosen by number a song title, artist and number of listeners will be displayed.

Flow of Application
The lib contains the api_manager.rb file, the cli.rb file, the environment.rb, top_songs.rb file and the version.rb file. All of these files work in tandem to control the flow of the application. The api_manager.rb is responsible for requesting and pulling data from an external source. The file is the key to gathering and importing information from a website of my choosing to my CLI app. The cli.rb is the heart of my app's control flow  and responsible for interfacing with the application and user. The CLI will prompt the user for input and will hang until the user types something and presses enter. The CLI gives instructions for the expected input at a given prompt.

Conclusion
After getting the program to actually run I refactored it by making the application DRY, meaning I tried not to use repeated code. My biggest challenges included finding a voable API to use and deciding whether to scrape a website or get the data from an external source using and API. This was a great exercise for practicing Ruby fundamentals and gaining more understanding of CLI File Structure.

Happy Coding!


