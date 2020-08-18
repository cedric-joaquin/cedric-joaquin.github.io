---
layout: post
title:      "Resellytics - Sinatra Project"
date:       2020-08-17 23:03:58 -0400
permalink:  resellytics_-_sinatra_project
---


Since we learned how to manage databases in the Sinatra module with ActiveRecord, I wanted to create something that was relevant and useful for me, some sort of collection-tracker. I like to collect and resell shoes as a hobby, and for the most part I've used a google sheet to track all my inventory and expenses. While it got the job done, it wasn't very pleasing to look at - so I figured this would be a good idea to use as my project, a web-app that provides analytics for a reseller -- ***resellytics***

## The App
When you first access the website you are greeted with the welcome page instructing you to login or signup for the app.

![](https://imgur.com/e8S3eXf.jpg)

Upon successful signup/login, you are redirected to your dashboard where a summary of your inventory and expenses are listed.

![](https://imgur.com/B8eyBg6.jpg)

Clicking on the Inventory or Expenses link will take you to their respective index page which shows you a full list of all your items. 

![](https://imgur.com/1SE2IAP.jpg)

From here you can select a specific item to edit its details, or remove it from your collection.

![](https://imgur.com/MvJx2rN.jpg)

![](https://imgur.com/ONbO4Qm.jpg)
## Challenges

This project was definitely easier than the CLI project. Having access to a lot of gems and frameworks specifically for web-apps helps tremendously, and I can see why many startups choose to use Sinatra/Ruby on Rails as their frameworks for initial development of their web-apps. It's quick to deploy with minimal hassle.

The biggest challenge for me was mainly UX design. I looked towards different dashboards of websites I used to get some inspiration on how an appropriate user experience should be. As a full-stack developer pushing web-apps you want to be able to not only have a functioning website but also a visually appealing and intuitive website. Otherwise, users will not be willing to give your product a chance.

## What I Learned
Although there weren't as many difficult challenges as the previous project, I definitely learned a lot more in this module. A lot of topics were briefly glanced over for this module since there was just so much to learn, and I had to supplement a lot of the lessons with research. Learning about the Client-Server Model was very interesting and also helped provide me with a brief introduction to HTTP requests and how the internet in general works - a big concept that is important to understand for building successful web apps. This is also very useful for my interest in developing ecommerce automation software in the future as I continue to learn throughout this program.

Learning MySQL and how to run queries before being introduced to ActiveRecord also helped me understand better how databases work and how information is pulled from the databases. It gave the proper foundation to understand and better use Object Relational Mapping (ORM) methods through ActiveRecord.

Sinatra I've learned is a very powerful and lightweight framework for quickly deploying a web-app. The best practices taught at Flat Iron provided me with an understanding of developing a web-app and made it not only easy, but also adhere to the standards expected of web developers. 

It definitely was a satisfying feeling to see your project come to life on a browser. It sure beats seeing it run through a CLI. 

## Improvements
I wish there was a section dedicated to front-end development, mainly with HTML and CSS - as I think that's something I'm lacking in. I definitely will continue to work on this app on the side as my goal one day is to create a fleshed out app that provides sneakerheads and resellers alike with the proper tools to analyze and manage their collection.
