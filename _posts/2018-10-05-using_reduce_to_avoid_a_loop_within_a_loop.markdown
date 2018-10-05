---
layout: post
title:      "Using .reduce( ) to avoid a loop within a loop"
date:       2018-10-05 17:46:01 +0000
permalink:  using_reduce_to_avoid_a_loop_within_a_loop
---


I was recently given the following white boarding challenge :

Given a the following array return a count of repeated items :

arr = [“a”, “a”, “a”, ”b”, ”c”, ”c”, ”c”, ”d”, ”e”, ”e”, ”e”, ”e”,]

My initial approach was this :

```
function countDupes(arr) {
  arrCopy = arr
  count = 1;
  for (let i = 0; i < arrCopy.length; i = i + count) {
    count = 1
      for (let j = i + 1; j < arrCopy.length; j++) {
        if (arrCopy[i] === arrCopy[j])
          count++;
      }
   if (count>1) {
   console.log((arrCopy[i] + " = " + count ));
   }
  }
}


```
This works fine but there is a problem: using a loop within a loop is creating high time complexity — O(n²).

This may be fine for an array of a few items like the example given — but when you are doing this operation to a list of say a million users you suddenly have a problem.

What this approach is doing is iterating over two arrays. For each item in the original array it iterates over the second array to compare. If it finds a match it ups it’s associated count by one then moves on to the next item in the array. So if you had an array of 4 items that is an iteration through the original array PLUS an iteration through the comparison array every time. We can cut this down greatly by using .reduce( ) — thereby reducing our time complexity.

The key to this is to generate an object that counts our total. As we interate through the array we generate our key value pairs :

```

arr.reduce( (count, element) => {
  count[element] = 1;
  return count;
}, {})
=> { a: 1, b: 1, c: 1, d: 1, e: 1 }
```



Notice the empty object. With reduce this is our initial value. We want an object as our initial value so we can increase our counts as we go with ONE pass through the array:


```
arr.reduce((count, element) => {
  if (!count[element]) {
    count[element] = 1;
  } else {
    count[element] = count[element] + 1;
  }
  return count;
}, {});
```


Here we go through the array check to see if the element as a key exists in our newly created object. If it does not we create it as a key value pair — element with a count of one. If it already exists we simply add one to our count.

The approach here is cleaner, easier to read and gets rid of the loop within a loop which is always a good thing !

Here are a few links I found that were very helpful in helping me understand .map, .filter, and .reduce :

https://codeburst.io/learn-understand-javascripts-reduce-function-b2b0406efbdc

https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d

https://medium.freecodecamp.org/reduce-f47a7da511a9



