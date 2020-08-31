---
layout: post
title:      "Creating a Basic Sinatra App "
date:       2020-08-31 17:47:06 +0000
permalink:  creating_a_basic_sinatra_app
---

First I want to admit learning and Building with Sinatra was a journey; Sinatra was a challenge but do-able. I had a bit of difficluty just understading how the SQL database works with Sinatra but I was able to figure it out and complete my project which I am so proud of.
I've grown as a developer during this jounrey and anyone reading this will learn from me. What exactly is Sinatra? Sinatra is a Domain Specific Language used for writing web applications written in Ruby.

I'm going to take you through my process of development. I started with a sketch on plain paper, because it's important to map out the layout of yoru design *prior* to writing any code.
I asked myself this basic question to spark my creative spirit; What do you care about? What are you passionate about? Next, I developed 2 models. I decided to use my newly learned Sinatra web application skills to build a Business Posting site. I'll explain my two models and their concepts below.
 
 # BizPlan Model
 ```ruby
 class BizPlan < ActiveRecord::Base
    # association macro
    belongs_to :user
    # model validations
    validates :name, presence: true
    validates :name, length: { minimum: 3}
    validates :mission, presence: true
    validates :mission, length: { minimum: 3}
    validates :budget, presence: true
    validates :budget, length: { minimum: 3}
end
 ```
I created a correspoding table for each of my model classes so they need to inherit from ActiveRecord. With this piece of code, I use macro to establish a relationship to a user. And I use bcrypt through ActiveRecord; using has_secure_password adds methods to set and authenticate against a BCrypt password. 
 
 # User Model
 ```ruby
 class User < ActiveRecord::Base
    has_secure_password
    has_many :biz_plans
end
 ```
 
I establish a relationship to biz_plans and also use has_secure_password to add methods to set and authenticate against a BCrypt password. When a user creates an account it must be with a unique login attribute. The job of ensuring the login is unique is left up to the controllers. Read below on how to set up your controller for authorization checks.
 
 
  # CRUD (Create, Read, Update, Delete) actions using Active Record
CRUD actions in the controllers connects views and erb files to certain actions in the controller. CRUD actions come with the sinatra-activerecord gem. CRUD routes are created in the controller for four unique actions; create, read, update and delete.
With the Create CRUD action we can create a table using a Rake task to create migration. In the controller I create a route get '/biz_plans/new', that renders the new.erb view. 
With the Read CRUD actions we can read or display information from our database. In the controller I create a route, the 'biz_plan_index' action, which should render the ERB view index.erb, which shows a list of all of the biz_plans.
With the Update CRUD action we can update information in our database using a form. In the controller I create a route get '/biz_plans/:id/edit', that renders the view edit.erb.
With the Delete CRUD actions we can delete information from our database using a form. In the controller I create a route delete '/biz_plans/:id', that creates a button and send the information to a form that will send a request to the delete controller action, where we will identify the biz_plan to delete and delete it.

When creating a Sinatra application, the file structure is very important. I used the corneal gem to set up my file structure for my project. I will break down the MVC File Structure below.
When I continue my build I must understand each file in our application will have a different responsibility and we'll keep these responsibilities split up into reasonable chunks. 
 # Steps
1. Create file structure using corneal gem in terminal. You can use this or manual create each folder. Corneal is just an easier way to handle this job.
2. Run bundle install in terminal, ensure versions are up to date. - set up gems
3. Set up Rake tasks, config folder and environment file
This is a very important file, is where you get your database connection ready, and it will connect your app folder with the rest of the files that require it as well.
4. Setting up config.ru file
5. Create a migration - create users table and biz_plans table with input for both
6. Create another migration
7. Create a User class - inherit from the ActiveRecord::Base class - set up validations
8. Create a BizPlan class
9. Create a users_controller - sessions and Validation
10. Create a biz_plan controller - Update, Delete, and Protecting Resources
11. Create Restful routes - explain Restful routes - User Signup and Password Protection
12. Set up views - Forms - error messaging
13. create BizPlans and users - use rake console
14. Run shotgun and test out as you build
15. Commit to GitHub Repo
16. Add styling with CSS
# Model, View, Controller (MVC) File Structure
Keeping Code Organized is so critical to the layout and flow of an application. MVC is used to help us with the organization. What is MVC? Model, View, Controller.
 
Controller actions are where the application configurations, routes, and controller actions are implemented. Controller actions represent the application logic. The "C" in MVC acts as the interface and flow of our application. Our "V" in MVC is out Views and holds the code that will be displayed in the browser. Models of our application represent the data and object logic of our application. Typically a Model includes a class used as a unit of measurement, it is the "M" in MVC.

Keeping our code organized is crucial when developing complex applications. As a developer I have learned the importance of separation of concerns and single responsibility.

```
├── apps
│   ├── Controllers
│   │   └── # Your controllers 
│   ├── models
│   │   └── # Your models
│   └── views
│   │   └── # Your Views
│   ├── layout.erb # the default html template
│
├── config.ru # Your Rack config
├── db
│   ├── development.sqlite# Sqlite3 database
│   ├── migrate
│   │   └── # Migrations
│   └── schema.rb
├── config
│   └── environment.db
├── Gemfile
└── Rakefile # Your Rake tasks
```
Separation of Concerns is again super important when building web applications. The views should never directly pull from the database. All of that should be taken care of in the controller actions, and the data should be passed to an erb file through a specific controller action.
# Project requirements - Build a full scale Sinatra application that uses:
- A sqlite database
- ActiveRecord
- RESTful routes
- Sessions
- Login/Logout

This is what I was tasked with and it can seem like a lot but once it's completely mapped out it because easy to understand how everything needs to work together. With the knowledge and understanding of your controllers views and routes in your app, you can truly create something amazing!

# What is REST?
A RESTful route is a route that maps HTTP verbs (get, post, put, delete, patch) to controller CRUD actions (create, read, update, delete). It helps us with data manipulation and by following it we are able to  create new content, edit content, and delete it.

HTTP verb: GET routes to '/biz_plans', action: index action, used to display all biz_plan only if you're logged in.
HTTP verb: GET  routes to '/biz_plans/new', action: new action, used to display create biz_plan form new biz_plan.
HTTP verb: GET routes to "/biz_plans/:id/edit", action: edit action, used to display edit form based on ID in the url.
HTTP verb: GET routes to '/biz_plans/:id', action: show action, used to display a biz_plan based on ID. 
HTTP verb: POST routes to '/biz_plans', action: create action, used to create a biz_plan
HTTP verb: PATCH routes to '/biz_plans/:id', action: update action, used to update an existing biz_plan based on ID. 
HTTP verb: DELETE routes to '/biz_plans/:id', action: delete action, used to delete a biz_plan based on ID.
# What are sessions and cookies?
Sessions and cookies work in tandem to store information about a user's interactions with a website at a given point in time. A session gives us a way to remember a user’s identity from page to page. Cookies and session data assists a web application in knowing who interacting with it. Cookies store information locally and are visible only to the server that created them. And while the web application on the server reads the client side cookie, it associates the cookie with an existing session (if such a session exists), and decides how to move forward. Pretty cool huh?

  # Why
 
The goal of this project was to build a basic Sinatra application by utilizing the Sinatra framework in conjunction with ActiveRecord and SQLite 3.
This Sinatra project is my very first web application -- completed with a database! 
# Look Ma, I built a website! 
Hope this post was helpful. Here I’m adding a link to my [Github repository](https://github.com/ameerrah9/BizUs) in case you want to check out my code and/or try out my Business planning app!


