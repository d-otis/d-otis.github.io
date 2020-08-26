---
layout: post
title:      "Rails and Javascript: Final Project"
date:       2020-08-26 15:13:39 -0400
permalink:  rails_and_javascript_final_project
---


## Overview
I was recently asked by a friend what it would take to make an equipment reservation system for their art gallery. The gears started turning and I wanted to take part of that domain as inspiration for my Rails and Javascript Final Project. Having started off with 6 models in my design phase I was advised to severely cut that down due to the complexity of it all being my first major JS project.

That was good advice.

What I ended up with was a Reservation System Lite. A small portion of the domain, but enough for me to really sink my teeth into what it takes to implement a JS front end that pulls from a Rails API backend using asynchronous API calls in direct response to user events.

## Features
Upon visiting the site. The user is presented with the option of navigating to either the Items index page or the Reservations index page. After the initial loading of all the JS script. The user does not ever need to refresh the page, making this a truly Single Page Application(SPA). When a User triggers any changes through CREATE, UPDATE, or DELETE actions, event handlers perform three basic actions:
1. A fetch call to the API with the appropriate HTTP verb
2. An update to our two global arrays: RESERVATIONS & ITEMS
3. Any appropriate DOM updates if the User flow hasn't caused the rendering of a new page "View."


### Items
* from here a user can easily select Items that are current available (not reserved) and then create a new Reservation
* just as easy the user can click the 'Add Items' button and add to the pre-existing Items inventory

### Reservations
* arriving at the Reservation index page a User is presented with the opition of Viewing or Deleting any of the listed Reservations
*  once triggering a DOM render of the Reservation Show action/view the User is presented with the option of updating the Reservation textarea and adding or removing an Item
*  if a User deletes all the Items the Reservation automatically is destroyed

## Process
Following the guidance of the curriculum, I started small: one modal, one controller action, one DOM manipulation. Beginning with Items seemed to make the most sense. I moved onto the Items Index action and then onto building out the Reservation model, its Index action and finally its Show action.

It's easy to devolve into some serious spaghetti-code moments when you're setting out to do something like this for the first time. I periodically checked in with my cohort lead, DJ. He recommended some best practices that had become habits to him: like using separate files, separation of concerns, and trying to make fetch calls as dynamic as possible for each HTTP verb.

Practicing the exercise of Red-Green-Refactor has proven to be incredibly beneficial in this SPA!
