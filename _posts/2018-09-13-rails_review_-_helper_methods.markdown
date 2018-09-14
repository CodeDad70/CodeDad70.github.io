---
layout: post
title:      "Rails Review - Helper Methods"
date:       2018-09-14 02:32:07 +0000
permalink:  rails_review_-_helper_methods
---


I was going back over a lot of Rails stuff this week to refresh. I have been so deep in React, JavaScript, GraphQL etc etc. over the past weeks  I felt it was time to step back to the back end and go over some Rails. 

I was going over my code for one of my projects and it reminded me of one of my favorite things if you are building your app's front end in Rails  .erb - helper methods ! 

It had been a while since I used them seeing as I have been using Rails mainly for an API and JS or React up front so when I was going through my code and saw them I thought " oh yeah these things are awesome ! " I thought I would share how I used them for anyone going through the Rails end to end part of the curriculum. 

Helper methods are great at cleaning up your code, keeping it dry, and readable ! They are your friend. 

The example for me came from an app I built that keeps track of your child's medication dosages and vital stats. These stats are shown on different cards for each age so the parent can look back and see for example how tall their kid was at 2 and how tall they are now at 4. Stuff like that. 

The tricky part was I wanted to be user friendly. Say the parent didn't feel like filling out weight for that certain card - they shouldn't have to. Problem is I also didn't want blank fields cluttering up my card layout. If they didn't put in a value for that stat I wanted it to simply not show up. 

You are thinking at this point " easy peasy genius - just if..else ... it  .  "   Which would work and actually did work - but it resulted in a giant sprawling card view .erb - there are a lot of stat fields to be filled or ignored. Also don't forget seperation of concerns... the less amount of logic you can have in your views the better. Keep it to showing stuff - not figuring out whether or not to show stuff. 

The simple solution is a helper method ! In the helpers folder I set up my cards_helper.rb and built out my methods for whether or not to show a field. A perfect example was the flu shot :

def flu_shot_given(card)
		if card.flu_shot == true
			"Flu shot ? Yes!"
		else
			"Flu shot? Not yet"
		end
	end
	
	Something was going to be displayed either way - I just returned the corresponding value to the view - the view is no longer concerned what it should show it just shows what it's told. 
	
	In the case of not showing a blank field it is was as easy as :
	
	def weight_check(card)
		if card.weight != ""
			"Weight: #{card.weight}"
		end
	end

I had a whole string of these for not only showing card stats but also things like profile stats for parents. I had one that parsed the date correctly for different displays : 

def short_age(card)
		card.age_create.gsub("year", "yr").gsub("month", "mo")
	end
	
	I even had one that changed from singluar to plural (child to children) depending on how many kids the user had :
	
	def many_kids
		current_user.children.count > 1
	end

Using these helper methods kept my code clean and let my views worry about only displaying the information - not parsing it !  It also makes the code so much more readable. You can pop over and see the helper methods right there in a row instead of spread out all over your code cluttering up your views.. it makes a world of difference !


