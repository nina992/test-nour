# Coding Test for Nour

## Mission

We want you to develop the frontend of an web application using React and Typescript.

## The Purpose of This Coding Test

We want to check your ability:

- To search what you don't know by yourself
- To understand the project's requirements and get yourself organized
- To be able build a functional frontend from scratch
   - However you don't necessarily have to implement all of the requirements perfectly within the term.

## Period

- 10 days (2021/02/11-2021/2/21 JST)
- Note: while you are working on this task we would like to do pair programming with you, so keep that in mind

## Specification

The Eukarya Bookshelf: An app that manages books for our in-house benefit system.

### Background

All fulltime members of Eukarya are able to request purchases of technical books that they are interested in by the company. The budget is 10000 yen per fulltime member. After commenting WHY they want the book, each application needs to get 2 fulltime member's comments approving the request. After buying the book the price of it will be subtracted from the total. Then, if he/she finishes the book and comments what they learnt from it, the cost of the book will return to their total.

### Necessary Features

* Design the UI based on the provided wireframe. But don't take too much time on the UI as we are more concerned about the functionality!
* Send post, edit, get and delete calls to the appropriate URLS with the appropriately formatted JSON
  * Get all applications
  * Get one application
  * Create application
  * Edit application
  * Delete application
* Users can only delete or edit their own applications.
* Users can comment on other user's applications as well as their own.
* If 2 or more comments on an application, status turns to buying.
* Each user has 10000 yen as budget and should appropriately subtracted or returned depending on books bought and reviewed.
* Users can't make a new application when their budget is lacking funds.

### Extra Features

If you can develop the following features too, you're awesome! (But it is not required)

* Write tests for appropriate components(using React Testing Library).

## Technical Stack Requirement

### React

- React v16.8~ (we highly recommend using React Hooks)
- Create React App (with typescript) is okay.
- Using a package like axios for API calls is okay.

### Typescript

- Typescript v4.5~

### Git

Please use github(this repo) for version control during this trial. Freely open issues for each part you will develop. When you finish an issue please open a Pull Request and we'll review it. Between here and Slack, we want to see how you organize yourself and communicate as a team member when necessary.

### Back-end

You don't need to develop anything for the backend. 

### API calls

- All API calls should respond with JSON.
- Auth and session management are not required.
- Please feel free to use whatever method you are familiar with for intercepting API calls(mock API server(MirageJS, json-server), etc)

* Applications
  * `GET /applications` get all applications\
  return
  ```
   [
      {
         "id": String,
         "createdOn": Date,
         "book": String,
         "amazon_url": String,
         "reason": String,
         "status": String, ("Applying", "Buying", "Reading", "Done")
         "comments": [Comment]
      }
  ]
  ```
  * `POST /applications` create a new application\
  send
  ```
  {
   "book": String,
   "amazon_url": String,
   "reason": String,
   "username": String,
  }
  ```
  return
   ```
    {
         "id": String,
         "createdOn": Date,
         "book": String,
         "amazon_url": String,
         "reason": String,
         "status": String, ("Applying", "Buying", "Reading", "Done")
         "comments": [Comment]
      }
  ```
  * `GET /applications/:id` get a single application
  * `PATCH /applications/:id` edit the application (status of application also can be edited here)\
  send/return
  ```
   {
      "id": String,
      "book": String,
      "amazon_url": String,
      "reason": String,
      "status": String, ("Applying", "Buying", "Reading", or "Done")
      "comments": [Object],
   }
  ```
  * `DELETE /applications/:id` delete the application\
  send
  ```
  {
   "id": String,
  }
  ```
  
* Comments
  * `POST /comments` create a new comment on the application\
  send
  ```
  {
   "username": String,
   "application_id": String,
   "comment": String,
  }
  ```
  return
  ```
   {
      "id": String,
      "book": String,
      "amazon_url": String,
      "reason": String,
      "status": String, ("Applying", "Buying", "Reading", or "Done")
      "comments": [Comment],
   }
  ```
  * `PATCH /comments/:id` edit the comment\
  send
  ```
  {
   "comment_id": String,
   "comment": String,
  }
  ```
  return 
  ```
  {
      "id": String,
      "book": String,
      "amazon_url": String,
      "reason": String,
      "status": String, ("Applying", "Buying", "Reading", or "Done")
      "comments": [Comment],
   }
  ```
  * `DELETE /comments/:id` delete the comment\
  send
  ```
  {
   "comment_id": String,
  }
  ```
  
* Users
  * `GET /users` get all users and all their applications\
  return
  ```
  [
   {
      "id": String,
      "username": String,
      "budget": String,
      "applications": [Application],
   }
  ]
  ```
  * `GET /users/:id` get a single user and all his/her applications\
  return
  ```
  {
      "id": String,
      "username": String,
      "budget": String,
      "applications": [Application],
  }
  ```
  * `POST /users`: create a new user\
  send
  ```
  {
   "username": String,
  }
  ```
  return
  ```
  {
      "id": String,
      "username": String,
      "budget": String,
      "applications": [Application],
  }
  ```
  * `PATCH /users/:id` edit the user\
  send
  ```
  {
      "id": String,
      "username": String,
      "applications": [Application],
  }
  ```
  return
  ```
  {
      "id": String,
      "username": String,
      "budget": String,
      "applications": [Application],
  }
  ```

### Other Info

* Create a new branch for each issue and process development (commit, push) in the branch.
* Open a new pull-request on this repository, and direct the PR to @HideBa, @Basel-Issmail and @rot1024

### OK

* You can use any websites that help you complete this trial.
* Clean code and writing test code is very welcome.
* Ask us on Slack if any part of the trial details are unclear.
* You can ask any question including technical topics as well, but we are also hoping to see how much you can figure out on your own.
