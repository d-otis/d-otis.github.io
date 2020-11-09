---
layout: post
title:      "React/Redux Final Project"
date:       2020-11-06 12:19:59 -0500
permalink:  react_redux_final_project
---


## Overview
My first apartment in Brooklyn seemed too good to be true. A recent gut-reno with modern appliances and hardware. What I didn't take into consieration, nor was I aware of, was the long standing issues and complaints levied against the real estate management company/owner. They were so notorious that they changed their name while we lived there to thwart all the bad reviews found by Google/Yelp. Not only that, but after we had finsihed our year lease and applied for the secuirty deposit to be returned to us, it took weeks to get to us because they mailed the check with only my name on the envelope and no mailing address.

Enter my final project: a Rate Your Landlord app!

## Features
1. Users should be able to visit the app and find reviews and ratings for properties they are interested in categorized by landlords/property owners. 
2. If a property or landlord isn't found that can create either, or both.
3. When a user leaves a review, a rating is required (5/5 scoring system). Once the review is saved the corresponding landlord rating and property rating are consequently updated system wide. 

## Process
I started with my backend models, relationships, and Postgres database before slowly integrating by React frontend with some minimal Bootstrap styling. 

One tricky aspect was making sure that attributes for properties and landlords were correctly updated on the backend as well as the front end. 

For my Rails API, I hit a lot of hurdles when it came to updating ratings using their before_action controller methods. After lots of headache, I scrapped using before_action and just triggered rating updates using instance methods in the Landlord and Properties model definitions. 

Within Redux on my front end I had to make sure that my Landlord reducer and Property reducer had case statements for '"ADD_REVIEW" in addition to their own model-specific CRUD cases.


