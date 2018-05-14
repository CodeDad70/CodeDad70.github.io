---
layout: post
title:      "Pass the props please!"
date:       2018-05-14 16:08:44 +0000
permalink:  pass_the_props_please
---


I was completely wrongheaded in my approach to React/Redux. It took me WAY to long to realize this. My moment I kind of got an "aha ! " was when I saw this :

 <SongCard history={this.props.history} song={this.props.song} />
 
 Up until that moment I my idea of dealing with React was - updating the state through my action calls then giving the next component access to the the state therefore having access to 'song'. 
 
 I was missing a whole channel of communication. I had a few calls like <DeleteButton song={this.props.song}/> but I was missing the significance of this in my thinking. By passing props directly from one parent component down the line to it's children you are **chaining them together**. The changes you make to the parent will move down the line to each component connected by this thread. 
 
 I know this is incredibly obvious but I was so head down in the weeds (this app was rough on me) that I missed this concept. I got it in my head that the store was almost a mini api in a way. Storing the song object's info to be accessed by each component independently. 
 
 When it clicked it was a full on Homer Simpson "Doh" moment ! Pass the props stupid. There is a thread that runs through your entire app from App.js all the way down to the delete button. Utitlize it - one change to the top effects change all the way down the line.
 
 Thus the name "React"
 
 "DOH !!!!" Facepalm .
 
 
