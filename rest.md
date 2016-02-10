# Note To Self - REST

## Table of Contents
  - [First Page](https://github.com/timurcatakli/note-to-self)
  





# What is REST?

## REST stands for:
REpresentational
State
Transfer

## What is it?
- It's not a formal protocol, but rather an "architectural style"
- A **convention** for mapping CRUD actions to HTTP requests
- It's stateless

## Why do we follow REST conventions?
- It's an easy way to structure a web application
- Helps us avoid URL chaos
- Makes API's easier
- It's one less decision we have to make when designing our routes

## HTTP Verbs & REST convention
- Let's say we have a collection of "dogs". Our application has full CRUD (Create, Read, Update, Delete) functionality for "dogs". In this case, our resource is a "dog". 

### GET
- "Get" me the document at this URL
- Used to request a single resource or multiple resources
- So, a GET request to `/dogs` displays a list of all dogs in your database.

### POST
- Create a new resource
- URL represents the collection
- Body is the data
- So, a POST request to `/dogs` creates a new "dog" record in your database.

### PUT/PATCH
- Replace (modify) a resource at this URL.
- So, a PUT request to `/dogs/4` updates the "dog" with the ID 4. 

### DELETE
- Destory a resource at this URL.
- So, a DELETE request to `/dogs/4` deletes the "dog" with the ID 4.

### How do you implement these RESTful routes in your application?
- Follow the conventions to make your code more readable, your routes easier to understand and follow!

![Imgur](http://i.imgur.com/0Zu9rHR.png)

### Nested Resources
- If you have a resource that can't exist without belonging to another resource, then it makes sense to "nest" them. Let's say within the scope of our application, we can't create a new dog unless we attach it to a breed. Here's the RESTful routing conventions we should follow and the purpose of each route:

![Imgur](http://i.imgur.com/pv2oTyv.png)

### Summary
- Follow these conventions when designing your routes and deciding what code to put within each route. If you aren't sure, ask!
- There are times when you might need to break these conventions, and that's okay - but try to follow them as much as you can.