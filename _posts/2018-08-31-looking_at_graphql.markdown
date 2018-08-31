---
layout: post
title:      "Looking at GraphQL "
date:       2018-08-31 16:57:38 -0400
permalink:  looking_at_graphql
---

This week I had a code challenge that involved using GraphQl with Apollo in conjuction with React at the front end. It is a LOT to pick up, so I thought I would share some of the links I came across while trying to figure it all out. 
This is far from comprehensive - just a couple code alongs I found super helpful as I tried to wrap my head around the post restful api idea .

First things first start here :
https://www.howtographql.com/

This has a good over view of how GraphQL works, what makes it different. On top of that there is a good tutorial to get you started.

I needed to work more on state management however so I started reading up on Apollo and how it deals with local state (think redux but instead of a store it's a cache) The Apollo docs are a good place to start :

https://www.apollographql.com/docs/react/essentials/local-state.html


The way Apollo manages state is VERY different than redux. It uses queries to retrieve data rom the state and mutations to write changes to your state. Resolvers are in a way like reducers in Redux - they take the action you assign and in the case of Apollo assign the proper mutation or query. 

This code along was a good step by step walk through of this and helped me understand the principles a bit:

https://hptechblogs.com/central-state-management-in-apollo-using-apollo-link-state/


Finally I found this multi part code along very very helpful. 

https://codeburst.io/graphql-and-apollo-client-by-example-part-1-3e0aec3eea71

It's pretty in depth - it not only goes over some simple toggle mutations (counter up / counter down) but also went through some implementations with forms that I found very helpful and couldn't really find anywhere else.  What is neat about this codealong is at the end the author refactors the code using Apollo boost - taking away some of the unecessary complexity. I found this really helpful as I was having dificulty understanding what boost did. 

Using a GraphQL, Apollo, and React stack is.... a lot. I have been very challenged by this and am not even close to fully understanding how the pieces fit together. The resources I listed went a long way in helping me at least start to wrap my head around the basics and I hope they help you !





