---
layout: post
title:      "A Quick Tip on Linking Images in React"
date:       2018-09-21 16:13:18 +0000
permalink:  a_quick_tip_on_linking_images_in_react
---


I'm buiding up a portfolio site and ran across a problem that took me some digging to figure out. I thought I would share what I learned. 

I am building a slide show type gallery in React and was trying to link some images. 

I tried the obvious and throught it would work :

 <img src={"./images/my_image.jpg"} />
 
 This didn't display the image instead showing me a broken image link so I started doing some digging. 
 
 On StackOverflow I found a thread about it with some helpful information. Basically when using Webpack you need to require images in order for Webpack to process them.  So your image tag should look like this :
 
 <img src={require('./images/my_image.jpg')} />
 
 I plugged my image path in this way and hit refresh and it worked ! Great and great... now i just needed interpolate the filenames into the path (I am switching between slides sort of like layers in React) and I'm good to go!  So I tried :
 
  <img src={require(`/images/${my_image_name}`) />
	
	Which promptly broke everything.  For good measure I tried :
	
	<img src={require("/images/" + my_image_name) />
	
	Which of course didn't work either. I was getting module errors. I began reading around and people were suggesting installing url_loader and file_loader and then changing my Webpack config folder :
	
	module: {
    loaders: [
      { test: /\.(png|jpg)$/, loader: 'url-loader?limit=8192' }
    ]
  }
	
	I used create-react-app to build my app however so accessing the Webpack config folder involved running npm run eject . There were warnings this was a one way street etc. 
	
	Things where looking pretty involved over just linking a few images but then I found a quick and easy fix without having to eject my config files! 
	
All you have to do is import the file path into your component - this allows Webpack to include the file in the bundle.
	
In your component import like this :
	
import React from 'react';
import my_image from './images/my_image.jpg'; 

Then inside your component you can use it like this :

<img src={my_image} alt="My Image" />

It worked perfectly for me - problem solved !

Reading a little more about things this approach might be a problem if you have a giant folder of images you need to access. You obviously don't want to try to bring them in as imports. When that is the case you will prob need to go the whole config Webpack route. 

However in this case I just needed to access a few slides so this was a perfect simple solution. 




	
	

