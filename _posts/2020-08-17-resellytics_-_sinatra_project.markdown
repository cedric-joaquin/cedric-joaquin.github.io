---
layout: post
title:      "Resellytics - Sinatra Project"
date:       2020-08-18 03:03:58 +0000
permalink:  resellytics_-_sinatra_project
---


Since we learned how to manage databases in the Sinatra module with ActiveRecord, I wanted to create something that was relevant and useful for me, some sort of collection-tracker. I like to collect and resell shoes as a hobby, and for the most part I've used a google sheet to track all my inventory and expenses. While it got the job done, it wasn't very pleasing to look at - so I figured this would be a good idea to use as my project, a web-app that provides analytics for a reseller -- *resellytics*

## The App
When you first access the website you are greeted with the welcome page instructing you to login or signup for the app.

!(https://imgur.com/e8S3eXf)

Upon successful signup/login, you are redirected to your dashboard where a summary of your inventory and expenses are listed.

![](https://imgur.com/71af8FE)

Clicking on the Inventory or Expenses link will take you to their respective index page which shows you a full list of all your items. 

![](https://imgur.com/1SE2IAP)

From here you can select a specific item to edit its details, or remove it from your collection.

![](https://imgur.com/MvJx2rN)

![](https://imgur.com/ONbO4Qm)

## Challenges

This project was definitely easier than the CLI project. Having access to a lot of gems and frameworks specifically for web-apps helps tremendously, and I can see why many startups choose to use Sinatra/Ruby on Rails as their frameworks for initial development of their web-apps. It's quick to deploy with minimal hassle.

The biggest challenge for me was mainly UX design. I looked towards different dashboards of websites I used to get some inspiration on how an appropriate user experience should be. As a full-stack developer pushing web-apps you want to be able to not only have a functioning website but also a visually appealing and intuitive website. Otherwise, users will not be willing to give your product a chance.

## Improvements
I wish there was a section dedicated to front-end development, mainly with HTML and CSS - as I think that's something I'm lacking in. I definitely will continue to work on this app on the side as my goal one day is to create a fleshed out app that provides sneakerheads and resellers alike with the proper tools to analyze and manage their collection.
