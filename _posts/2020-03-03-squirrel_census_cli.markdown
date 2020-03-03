---
layout: post
title:      "Squirrel Census CLI"
date:       2020-03-03 16:34:01 -0500
permalink:  squirrel_census_cli
---


## Features/Overview
* List quantities of reported primary fur colors
* List the max amount of squirrels per hectare
* Programmatically display the total number of squirrels and the total number of dates.
* Help displays the list of commands again for the user
* Programmatically displays all 11 dates and how many squirrels were spotted on each day
    1. Allows user to pick day from list
    2. Squirrel list based on sightings that day is displayed
    3. User picks specific squirrel
    4. Squirrel attributes is programmatically displayed
    5. User is asked if they want to drop a pin on Google Maps where that specific squirrel was seen
    6. If yes, user’s default browser is opened and Google Maps loads with pin dropped exactly where squirrel was counted

## Process

I leafed through the datasets on NYC’s Open Data project and settled on the squirrel census since my partner and I have a running inside joke about an urban squirrel expert that we both know. I signed up for an app token and familiarized myself with the JSON output deciding how I was going to digest and use this data in my CLI. It was immediately apparent that I create a `Squirrel`, `Scraper`, and `CLI` class.

The `Scraper` class, of course, does the scraping and builds a hash that is ingested by the `Squirrel.new` using mass assignment. Specifically the `#get_squirrel_aoh` creates an array of hashes. One hash for each squirrel. And the `#create_squirrels_from_aoh` then creates a new squirrel for each hash in the array of hashes.

The `Squirrel` class would take care of each instance of a squirrel using `attr_accessors` for 26 of the attributes provided in the API. The majority of the methods are class methods since I am operating on the squirrel population on a whole, rather than individual squirrels. Class methods included grouping squirrels by date for displaying to the user, creating hashes of fur color, squirrels per hectare, ages, and sighter shifts to be used in printing methods for the CLI user.

The `Date` class was conceived later on in the project in an effort to flex my collaborating object skills. The census lasted 11 days in Central Park in 2018. I figured that each squirrel instance has one date instance and each date instance has many squirrel instances. In order to make the date an object that is only created once (since a date in time can only happen once, unless we are inside a limited HBO) inside my `Squirrel` mass assignment I have a conditional that treats the date key in a special manner. It takes that date string and checks the `Date.all` array to see if a `Date` object instance exists with the that exact value for the date attribute via `Date.find_or_create_by_date` class method. If the date already exists the `Date` instance adds the squirrel to its list of squirrels, if it doesn’t exist it creates a new `Date` instance and then adds the squirrel to its list of squirrels. Both forks of that conditional return the date object, new or old, and assigns that object to the date attribute in the respective `Squirrel` instance.

The `CLI` class is our *controller* of the entire process. It presents the user with all their command options and subsequently calls instance methods on itself that use class methods from every other class. It’s called from the `squirrel_census` executable file in the `bin` folder. The `CLI` also is responsible for initiating a new scrape at the beginning of each time the program is ran.

## Obstacles
Nothing really to report in terms of obstacles except that I had some difficulty wrapping my head around the name spacing when attempting to create a module that could be used throughout each class that simply provided a `spacer` method to print an empty string for UI friendliness. Wasn’t able to implement this unfortunately. Getting the collaborating objects up and running so that they each knew about each other in appropriate ways was also touch and go for a bit, but I managed to pull it off!

When implementing the `open_location_in_google_maps` class method I had a bit of trouble before I realized that the provided coordinates needed to be reversed. In the API `x` is listed first, but Google Maps’ URL scheme requires the first number in the API to be listed second, or else It would drop a pin in Antarctica, literally. I’m used to points on an x/y chart listing their horizontal coordinates first but mapping is apparently reversed!

## Links
[Squirrel Census CLI Walkthrough](https://www.youtube.com/watch?v=DyxNOYZZHww)

[Squirrel Census CLI Github Repo](https://github.com/d-otis/squirrel_census_cli)
