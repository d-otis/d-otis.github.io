---
layout: post
title:      "Sinatra Final Project"
date:       2020-04-28 19:55:02 +0000
permalink:  sinatra_final_project
---


*Project:* A simplified version of the popular application submission service, SlideRoom. In this project I’m framing the use of the service in relation to an artistical call from an arts institution to take submissions for an exhibition. Artists can create accounts, login and create/view/edit/delete their own applications. Each application features fields for Submission Title, Artist Statement, and a URL for a photo that showcases their work in each application.

I started this project with a concept that more closely mirrors the full complexity of the real service, but was advised to simplify it and save that complexity for my Rails app potentially.

1. I sketched out my Models and their relationships using white-boarding and eventually an online ERD program, taking time to research how to properly demonstrate relationships using ERD conventions (IE: cardinality connections etc)
2. Afterwards I stubbed out my environment, Gemfile, and Rakefile
3. Once I was sure I had the relationships properly defined I created their respective migrations and used relationship macros and validations in the models.
4. Before moving onto controllers + views I verified the behavior of my models and their relationships in console.
5. From here I implemented all CRUD actions for Artist and Application classes
6. I insured against URL hacking and resource ownership validations for Artist and Application controllers
7. Implemented message for success/errors for Application and Artist resources.

*Looking Ahead:* If I were to take this project to the next level I would add the ability to add multiply photos to an artist’s application. There would also be another class of User: Institutional Admins that would be able to view all submissions per Submission Call and view all their artists per Submission Call and per institution.
