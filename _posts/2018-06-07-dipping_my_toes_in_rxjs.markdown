---
layout: post
title:      "Dipping my toes in rxJS"
date:       2018-06-07 15:40:52 +0000
permalink:  dipping_my_toes_in_rxjs
---


I attended a meetup recently in Durham as part of the Google Developer Group Triangle meetings. One of the organizers gave an interesting talk about rxJS and it's use in reactive programming. 
I decided to check it out and while I've only scratched the surface so far, what I've seen is very impressive... 

Reading over the documentation I found this very cool code along tutorial for creating a RSS reader using rxJS :
https://github.com/channikhabra/yarr

The funny thing is I'm only in the introductory chapters (it's long ! ) I haven't gotten to the main section yet, but I'm already impressed. 

In the tutorial you first create a counter usent setInterval and the virtual DOM 

let render = (count) => <h1 className='hello-world'> Hello World {count + ''} </h1>;
let count = 0;
let view = render(count);

let rootNode = createElement(view)
document.body.appendChild(rootNode);

setInterval(function() {
    count++;
    let newView = render(count);
    let patches = diff(view, newView);
    rootNode = patch(rootNode, patches);
    view = newView
 }, 1000)


Now here is the same counter using an RxObservable:

let render = (count) => <h1 className = 'hello-world'> Hello World {count + ''} </h1>;

let view = render(0);
let rootNode = createElement(view);
document.body.appendChild(rootNode);

Observable
  .interval(1000)
  .map(n=>render(n+1))
  .subscribe (
    newView => {
      let patches = diff(view, newView);
      rootNode = patch(rootNode, patches);
      view = newView;
    }
  ); 
	
	Look at how clean and concise that is ! I'm very excited to learn more about Observables. Big shout out to https://github.com/channikhabra for creating an awesome tutorial. I'm looking forward to continuing my way through it. 
