---
layout: post
title:      "Fetch and the Promise"
date:       2018-05-14 15:54:41 +0000
permalink:  fetch_and_the_promise
---


The power of Fetch is that it is a promise object. The promise object REPRESENTS a value of a request that is not yet available. The allows for flexibililty with your asynchronous action requests because your code isn't breaking the second it isn't receiving it's request. Fetch in effect tells it to chill out and let's it know what is coming - it keeps everyone happy until the request comes back. 

Fetch is also a thenable object which means once that promise IS fullfilled you can chain together your .then calls. The key here is **each then call receives the result of the previous one as its argument.** Which means you can render your repsonse to json and - THEN pass that json response to a different action which in turn sends that json to your reducer. 

In  a way the by chaing your then call you are taking the asynchronous nature out of your action requests and creating a chain of events you want to happen once your promise object receives this request. 

An example of this in my react app was the delete action I have. It took me a bit to figure it out - I was trying at first to make an action request of deleteSongUpdate which was sending a request to the reducer to filter out the deleted song from the list of songs in the state and update the nav bar and tabs being displayed.
It was incorrect to do it from the onClick in the deleteSong component because the fetch request had not yet received the promise back from my fetch request. 
What fixed it was first sending the destroy request - THEN rerouting to the index page using history.push and then finally saying, "oh and while you are going to the index page re-render the list of songs minus the one just deleted. " 

Fetch being a promise object essentially held the error at bay until it's promise came back and then chained together the appropriate action calls needed to render the nav list and index page the correct way with the deleted song removed.



