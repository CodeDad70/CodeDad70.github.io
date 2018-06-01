---
layout: post
title:      "Big O - Solving the Algorithm isn't enough"
date:       2018-06-01 15:46:36 +0000
permalink:  big_o_-_solving_the_algorithm_isnt_enough
---


During my mock tech interview I was asked to solve a problem. Basically giving an array - sort through it and give the number of duplicates integers within that array. 
I chewed on it a bit and came up with what I thought was a passible answer. I basically interated over the array twice and compared the arrays to each other using .filter to grab the duplicates. Get a count of those duplicates and done. 
So I thought. 
My mock interviewer told me it the time complexity was too high. This was not something I had even considered but as he walke me through it things made sense. 
Basically my approach would not scale well. Iterating through the same array twice to compare it to itself works fine with an array of say 5 numbers. When you start scaling up to big numbers you are suddenly doubling a huge amount of bandwidth and processing power. This will not do. 
I've begun reading up on time complexity now and it's a very good lesson to learn. I think approaching things in the most efficient way possible is an ongoing challenge and a learning process.  I'm grateful to my mock inteviewer for alerting me to this however, I can begin thinking about things with that goal in miind. 
It will help me write more effiecient code and force me to think about things in a more critical manner - which I think is always a good thing !


