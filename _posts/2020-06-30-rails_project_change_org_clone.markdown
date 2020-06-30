---
layout: post
title:      "Rails Project: Change.org [clone]"
date:       2020-06-30 11:52:14 -0400
permalink:  rails_project_change_org_clone
---


## Domain: Petition Website

### Features
#### Users
* create User through sign up form and Facebook OAuth strategy via omniauth gem
* edit/update user info: email + password
* show: displays user's authored petitions and petitions the user has signed

#### Petitions
* create/edit Petition with title, description and a signature goal
* petitions#index that show petitions @ a glance in reverse chronological order
* special routes: petitions/goal-met and petitions/most-signatures

#### Signatures
* create and delete signature which is a join model for petitions and users with added fields for an anonymous listing option and message


### Overview
Inspired by the present moment I chose to model my domain on popular petition websites like Change.org and MoveOn.org

A user can join manually via the form or through an OAuth strategy via Facebook. 

From onboarding they can create petitions and sign the authored_petitions of other users. Signatures act as joins between users and petitions with extra fields of a message and boolean that determines whether your name and message are displayed in association with a petition that you've signed.

### Process
I started with the User model as they are the owners of all other models. From there I moved to the Petition model experimenting with ways to alias a Petition instance in relation to a User so as to refer to a Petition that a User owns in a more semantic way as to avoid confusion with a Petition that a User has signed. I solved this by utlizing ActiveRecord macros and aliasing Petitions that a User owns via User(instance)#authored_petitions and vice versa a Petition's #author that refers back to a User via #author_id

I made sure to allow destruction of dependents on removal of Petitions/Users. If a User is deleted all associated #authored_petitions and their signatures are destroyed. If a Petition is deleted all associated signatures are also deleted.

I followed-up the app build with some styling via Bootstrap to try to mimic the overall vibe of Change.org
