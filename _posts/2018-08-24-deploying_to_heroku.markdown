---
layout: post
title:      "Deploying to Heroku "
date:       2018-08-25 03:24:43 +0000
permalink:  deploying_to_heroku
---


This week I needed to deploy an app I had built to Heroku. The app was had a React/Redux front end that communicated to a Rails API backend. 

I struggled a bit to get everything to work so I thought I would share some quick tips that I figured out throught a LOT of trial and error. 

First off - I found these two guides very helpful. 

https://medium.com/@siobhanpmahoney/deploying-a-react-frontend-rails-backend-project-to-heroku-4b2c4f6f630c

https://medium.com/@nothingisfunny/deploying-rails-api-and-react-app-to-heroku-from-a-single-github-repo-7d8597abc55a

Those are both good places to start. 

The biggest thing to remember is create TWO seperate Heroku apps. Get them working individually before you try to wire them together. 
You should be able to got to https://my-heroku-app.herokuapp.com/users  and see your JSON list of your users just like if you were hosting locally. 
Also you should be able to run your front end app on it's own.  Things will break when you make back end fetch requests, but make sure things are working up to that point. 

If both apps are working seperately it is really a matter of changing the URL of your fetch requets in the front end from "localhost.3001/api/myrequest " to the url of your Rails API .  ie:  https://my-heroku-app.herokuapp.com/users

A COUPLE TIPS - 

Don't forget to change your CORS config file in your Rails app !!!  
You will need to change this from  

Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do 
    origins  'localhost:3000'
		
		TO:
		
		Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do 
    origins 'https://your-heroku-app.herokuapp.com'


This can be really frustrating. You change all your fetch request urls - but still are getting 404 errors and can't figure out why. 

ALSO - and this one took me a TON of trial and error and misery. You may read about procfiles especially for your Rails app. If you set up your Rails app as an API you DON'T need one.  I was getting a ton of weird 500 errors from my API, some post requests were going through but deletes were not etc . I had added a procfile to basically run my rails server .It was a confusing mess because some fetch requests would work and others would not. Out of frustration I reverted to before I added a procfile and voila everything worked. The React making a fetch request will wake up your Rails server - you don't need a procfile.

I didn't go through deploying these individual apps to Heroku because I would basically just be re-typing the above articles. Just follow the steps on those to deploy and you shouldn't have too much trouble running your apps alone. They are very straightforward.

The added tips I mentioned were things I ran accross that caused me some pretty sever confusion - I hope this helps make deploying your app a little easier !



