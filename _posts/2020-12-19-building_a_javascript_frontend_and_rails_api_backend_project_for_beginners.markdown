---
layout: post
title:      "Building a JavaScript frontend and Rails API backend Project for Beginners"
date:       2020-12-19 21:15:20 -0500
permalink:  building_a_javascript_frontend_and_rails_api_backend_project_for_beginners
---


Fresh Find application is a web application using JavaScript to render frontend data and Rails API to manage backend data.

[](https://blogs.luc.edu/farmersmarket/files/2020/06/Produce-1140x550.jpg)

Farmers, use the Fresh Find application to keep track of your inventory when your next Farmer's Market rolls around!
Create a "Produce List" using your choice of name, then simply add items to your list.
For Flatiron School's Software Engineering course project 4, I decided to have two separate repositories for my frontend along with my backend. This avoids issues of hosting on a deployment site such as Heroku. This also allows me to run both my backend and frontend at the same time, with the Rails server running on localhost:3000 and the front-end Javascript and HTML/CSS running on the browser. This allowed for faster error handling because of the use of the Console in the browser and being able to go into the Rails console at any moment. When I was setting up my Rails API, I had to make use of the - api Flag like so.
```
rails new fresh-find-backend - api
```
This - api flag ensures that I create an API only application using Ruby on Rails.
This project uses AJAX and JavaScript to make fetch requests to a Rails backend to access a database containing information about Farmer's Market items. I used JavaScript to make changes to the DOM. Javascript is powerful and capable of so much. This JavaScript Project requires that the app use a Javascript frontend with a Rails API backend. Client/server interaction must be handled asynchronously in JSON format. The Rails backend needs to have a resource with a has-many relationship and have at least 3 AJAX calls (at least two of Create, Read, Update, and Delete). This was by far the toughest part of the course, combining both JavaScript and Rails.
My JS + Rails API project is a Farmer's Market vendor's dream. My app allows vendors to keep track of their inventory by creating lists for their items they'll be selling at their upcoming Farmer's Market visit. The object model relationship is a list has many items.
# Three Pillars of Web Programming
Recognizing JS events, Manipulating the DOM, and Communicate with the server. All of these pillars were difficult for me to grasp at first but with persistence, I was able to learn these pillars.
My application has two classes, List and Item as show below:
```
class List { 
 static listNames = []
 
 constructor(list){
 this.id = list.id
 this.name = list.attributes.name
 this.items = list.attributes.items
 List.listNames.push(this)
 }
}
```
```
class Item {
 constructor(item) {
 this.id = item.id
 this.list_id = item.list_id
 this.content = item.content
 this.li = document.createElement('li')
 }
```
# Making sure back end is connected to front end
In order to connect my frontend directory to my backend directory I needed to make use of a fetch request to my Rails API backend from my JavaScript frontend. Using the http://localhost:3000/lists as my endpoint. I connect the front end of my application to my back end using the following GET fetch request:
```
static getLists() {
 fetch(listsURL)
 .then(resp => resp.json())
 .then(lists => {
 for(let list of lists) {
 let newList = new List(list.data)
 }
 this.renderLists()
 })
 }
```
This is also an example of a static method in JavaScript. With the data I receive from my back end server, I am then able to handle DOM manipulation and render this data to my HTML.
My classes contain functions that strictly handle DOM manipulation. Some functions handle server communication. Some functions may serve as 'helper' functions to others. This all ties into the programming mantra of "Separation of Concerns". With Object Orientation, instead of a web, we can think of our code as a collection of cells. These cells are separated from each other, can contain information, bits of data like variables, as well as behaviors, functions directly related to that data. 
# Static Methods - OOJS
Static methods are class-level methods - they are not callable on instances of a class, only the class itself. These are often used in 'utility' classes - classes that encapsulate a set of related methods but don't need to be made into instances.
```javascript
class StaticMethod {
 static methodName() {
 console.log("My method is static!");
 }
}
```
I hope you learned something about JavaScript and Rails reading this piece on the fourth software engineering project for Flatiron School. This was by far the toughest part of the course, combining both JavaScript and Rails. I learned a lot about utilizing classes in JavaScript and handling JSON formatting.
Source Code https://github.com/ameerrah9/Fresh-Find-Frontend
Happy Coding!

