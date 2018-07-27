---
layout: post
title:      "Using the react-rails gem"
date:       2018-07-27 20:36:38 +0000
permalink:  using_the_react-rails_gem
---


This week I have been doing several code alongs to keep things fresh in my mind and to learn some new techniques. 
As I was searching around I found a very cool blog on Medium about using the react-rails gem to create a CRUD app. 
When I started reading it I was happily suprised to see it was written by a fellow Flatiron grad ! (shoutout to Lucya Koroleva)
It's a very cool article which you can check out here :
https://medium.com/quick-code/simple-rails-crud-app-with-react-frontend-using-react-rails-gem-b708b89a9419

The basic jist of it is instead of the usual approach of creating an api in Rails then creating a seperate React frontend you can use the react-rails gem to create React components DIRECTLY in your Rails Js asset pipleine !
This seems very useful for smaller projects and will make things like deployment much simpler.

This short versino of how to do it is to create your Rails app and install the react-rails gem. 
One tricky part is you need to change your application controller to :

class ApplicationController < ActionController::Base
 protect_from_forgery with: :null_session
end

You then go about setting up your rails app with a namespaced API controller as usual 
(class Api::V1:: YourController < ApplicationController)

Create your CRUD actions as you normally would (dont forget to render json)

Namespace and set your routes as your normally would for an api.

One more bit of difference is you need to set up a HomeController top level in your controller folder:

class HomeController < ApplicationController
  def index
  end
end

set your root:
 root to: 'home#index'
 
 Then you make a home folder inside your views with an index.erb.html file. In that file you put:
 
 <%= react_component 'Main' %>
 
 Inside your javacripts create a components folder and create your first component named Main.
 
 (!!!!) Crazy. 
 
 Start building away at your React components freely. 
 
 I obviously gave the very abridged version of how to do this, but I wanted to show how really simple it is to get this going. This full blog post go over everything in great detail and is really worth checking out. 
 
 Thanks Lucya !!
 
 
 
 


