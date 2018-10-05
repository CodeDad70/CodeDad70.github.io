---
layout: post
title:      "Conditionals with React-Spring"
date:       2018-09-29 14:51:23 -0400
permalink:  conditionals_with_react-spring
---


I have been using the excellent React-Spring for animations on a portfolio site I’m building. I wanted to create some conditions for certain slides. For example the first slide in the component would not have a back button, but the second would.

It’s pretty easy to do with React-Spring, here’s how I did it:

Say you are creating a parallax effect to bring slides in and out. Using React-Spring it would look like this :

```
<Parallax className=”container” ref=”parallax” pages={7} horizontal scrolling={false}>
  <Page offset={0} background = “slide-one” frameOne = “frame-one” imagelink={slideOneA} caption=”Here is the first slide” first-line=”Slide desription goes here” onClickForward={() => this.scroll(1)} />
  <Page offset={1} background = “slide-two” frameTwp = “frame-two” frameThree = "frame-three" imagelinkA={slideTwoA} imagelineB = {slideTwoB} caption=”Here is the second slide” first-line=”Slide desription goes here” onClickForward={() => this.scroll(1)} onClickBack={() => this.scroll(0)} />
</Parallax>

```
Notice that there are two slide for this example. The first slide does not have an onClickBack even listener as it is…well.. the first slide. I’ve also put multiple images in the second slide.

We basically create a Page function that brings in the params from our exported slide (note the offset number is used to keep track of which slide we are referring to) :

```
const Page = ({ offset, caption, first,  background, imagelink, imagelinkA, imagelinkBframeOne, frameTwoonClickForward, onClickBack }) => (
  <React.Fragment>
```


Now we can set our layers to behave according to the properties we pass to it:

```
<Parallax.Layer offset={offset} speed={0.2} >
<div className={`layerBackground ${background}`} />
</Parallax.Layer>
The background will change according to the .css style we assign to it using className and define in our stylesheet. You can change background color and properties for each slide this way.

<Parallax.Layer offset={offset} speed={0.4} >
  {offset!==0 &&
    <Icon path={mdiArrowRightThick} className = "arrow-back" 
    size={1.5} rotate={90} color='black' onClick={onClickBack}/>
  }
  {offset!==6 &&
    <Icon path={mdiArrowRightThick}  className = "arrow-forward" 
    size={1.5} color='black' onClick={onClickForward}/>
  }
	
```
	
Here’s where our conditional comes in. In this snippet we are saying “if the offset number is not 0 (the first slide) dispaly a back arrow . Also if the offset number is not 6 (last slide) show a forward arrow. “

It’s pretty much that simple. You can extend this as I did with frame numbers with something like this:

```
<Parallax.Layer offset={offset} speed={1.5} >
  {offset===1 &&
    <div><img className={`image-frame ${frameTwo}`} 
    src={imagelink}    alt="Layout"/> </div>
   }
</Parallax.Layer>
<Parallax.Layer offset={offset} speed={1} >
  {offset===1 &&
    <div><img className={`image-frame ${frameThree}`} 
    src=  {imagelinkB} alt="Layout"/></div>
  }
</Parallax.Layer>
```

What we are doing here is saying “ if the offset number is 1 assign image one to the image we defined in our offset one to frame one and assign image two to the second frame. “

We can then alter frame sizes and position in our stylesheets using className. This allows for custom design for each slide so you don’t have the same layout over and over in your carousel.

React-Spring is a great tool for animations within React, I recommend it highly. Using the little tricks we just went over it can become a pretty versatile tool as well.
