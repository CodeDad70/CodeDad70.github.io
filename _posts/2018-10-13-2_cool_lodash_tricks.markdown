---
layout: post
title:      "2 cool Lodash tricks "
date:       2018-10-14 01:53:58 +0000
permalink:  2_cool_lodash_tricks
---



I have been recently playing around with Lodash. Lodash is a JavaScript library of utility methods. It takes common, often repeated methods we use in JavaScript and simplifies them and in a lot of cases adds funtionality. Using Lodash can greatly reduce boilerplate code and get rid of side effects (think functional programming ! )

Here are a couple real quick examples- 

-The for loop -

You know it - you love it. You type it out a billion times :

```
for ( let i = 0; i < 5;  i++) {
  
}	
```

using Lodash that becomes :

```
_.times(5,  function() ) {
      
}
```

This removes the extra i variable which can create scope problems and just looks nice and clean !!!



-Random number -

The usual approach to a random number for 0-10 is something like :

```
Math.floor(Math.random() * 10+1)
```

Lodash is simply :

```
_.random(10)
```

Need a random number between 5 and 10 ? Easy :

```
_.random(5,10,true)
```

I went over just a couple real simple, very common examples to illustrate how simple using Lodash is. There are a lot of really interesting utilites Lodash can handle - a lot dealing with objects. Things like extending objects, removing properties from objects,  and selecting specific properties from one object to create another to name a few.  It can even help simplify error message when parsing .JSON. 

I have really just begun to explore Lodash, but the more I learn about it the more impressed I am with it's features. It is a powerful tool that I plan to utilize in my everday JavaScript coding !





