---
layout: post
title:      "Breadcrumb trails to save your sanity"
date:       2018-08-18 02:20:32 +0000
permalink:  breadcrumb_trails_to_save_your_sanity
---


I had a code challenge to complete this week. I decided to build it out using React/Redux on the front end with a Rails API on the back end for persistence. One of the problems I often run into building out a front end with React/Redux is following the data flow.. which values are going where at what point can be a bit of a challenge. Making sure the correct data is being passed through props and other components are updating state can be like untying a knotted up thread.

This time around I came up with a fairly obvious trick - but it really helped me out a LOT and I thought I'd share...
ready? 
console.log 
Ha ! Yeah I know obvious... but here's what I mean  - 

As I was building out the front end I stopped and took the time to put console.log at a bunch of different points througout the app. They key here is to LABEL them and put them in as you go :

console.log( " Inside the getValue action creator : ", value)  

I left them like a breadcrumb trail throughout my app....  inside the render of components, inside action creators and inside my reducers. 

It gave me a visual chart of how my values were moving which really helped. If things where breaking or acting unexpected I could look through my logs and look for a value that came back undefined - it was almost always a good place to start. 

I realize debugger can do a lot of other things in this regard (also redux dev tools) - but I like how console.log doesn't freeze - it runs the entire data flow and helps me invision how my app is working. 

It's also so easy for me to mess with and change values to see if it fixes things. If console.log(" inside card render", this.props.card) comes back undefined I can quickly just change my log to console.log(" inside card render", this.props.card.value) to see if that changes anything - WITHOUT MESSING WITH MY ACTUAL CODE. I went as far as to .map values in logs to see what was happening  - console.log("inside card render", this.props.cards.map(card=> card.title)) to see what it was giving me. It saved me a ton of time instead of putting a map function in my code to find out it was broken etc and have to revert to where I was. This is especially helpful in React where other parts of the puzzle can be messing up your return - change a few logs and see what happens, no code gets messed up. 

I found it really helped me a lot this time around and saved me a lot of frustration. Next time you are putting together a React app take a second to throw a bunch of console.logs in as you are writing your code. 

It can be a pain to have to go find them to take them out (don't forget to label where they live !!) but it will ultimately save you a lot of hair pulling and heartache !


