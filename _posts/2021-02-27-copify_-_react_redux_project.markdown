---
layout: post
title:      "Copify - React Redux Project"
date:       2021-02-27 20:07:37 +0000
permalink:  copify_-_react_redux_project
---


For my final project I wanted to do a revamp of a previous project for Inventory Management and Analytics for Shoe Resellers. Although realistically, this app can be used for any type of reselling.

You're first introduced to your Dashboard. The dashboard shows the analytics of your inventory, including your total inventory value as well as amount of items in your inventory. 

![](https://imgur.com/Lp24UIe.png)

Navigating through the app is simple through the NavBar on the left. Navigating to the Inventory section you're shown a detailed list of all available items

![](https://i.imgur.com/GZKferX.png)

You're able to select specific items in your inventory, and a new React Component will be rendered below the table. This utilizes client-side routing through the [React Router](https://reactrouter.com/) framework.

You're able to edit and delete existing items as well as add new items to your inventory. 

What's great about using React-Redux is the flexibility it gives to your app. Compared to using the Sinatra or even Ruby on Rails front-end framework, your app can be a lot more dynamic. With the help of the React Router framework, you can take advantage of client-side routing - preventing the need to unnecessarily reload pages every time you hit a new URL. Instead, the client will render specific components of your app depending on which Route is hit.
