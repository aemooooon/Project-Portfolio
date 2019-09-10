---
layout: post
title: The Sprint 2 Summary
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-08-22
color: brown
---

We have already started the second Spinrt, after the first debrief. A total of 9 issues, I have focus on user sign up, login and user authorization, and navigation features. 
Because we have some other screens in addition to the map on the homepage, in order to facilitate the display to the customer, but also convenient for our own debugging, the addition of navigation is imperative.

Carthur has been responsible for the map area geofencing feature and track the user's current location. At the same time he will be able to add Marker to the map and save position coordinate data to the database. A detailed list will be listed below:

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/035.jpg?raw=true "sprint 2 screenshot")

### Hua Wang
* feature 14 - adding navigation bar/menu
* feature 13 - validation for input authentication fields
* feature 12 - separating sign up and log in 
* feature 16 - Add Navigation to Home page

### Carthur
* feature 15 - migrating from cli to expo development environment
* feature 15 - adding latitude/longitude coordinates to the database
* feature 11 - Add running location to map as different markers
* feature 8 - track location of users
* feature 3 - add geofencing


At the same time, we did another thing. Since we all have our own computers and computers in the school project room, maybe the version and hardwares of each computer are different, which leads to problems in our development. So I discussed with Carthur and decided to change our current Android Studio and React Native CLI partern to EXPO CLI mode, so we don't have to rely on Android Emulator. 

Another reason is that Android Emulator can't get the user's current location, so that will brought a lot of inconvenience to us in the future The test . If we use the real phone test, it is directly what the user wants, Carthur has IOS, and I have Andriod, such a perfect way.



