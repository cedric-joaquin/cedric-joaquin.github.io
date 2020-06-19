---
layout: post
title:      "CLI Project - Auto Checkout App"
date:       2020-06-17 21:50:19 -0400
permalink:  cli_project_-_auto_checkout_app
---


## The Process

For the CLI project, I decided to create an app that scrapes the Supreme store website. I chose to go this route due to my interest in shopping automation. The first step to that is learning how scraping websites work and how to store that info.

I would say writing the scraping portion of my project took a good chunk of my time. I wasn't familiar with HTML and CSS that well so I spent a lot of time testing if the CSS selectors I chose were scraping what I wanted. In order to obtain all the product info I needed (Categories, Products, Colors, Sizes) I had to scrape multiple webpages. Each category had its own webpage that listed the products available.

![](https://imgur.com/a/v7gOAu8)

The tops/sweaters webpage listed all products available along with their styles. However, to get the available sizes for each unique product/style combination, I had to access each individual products webpage. This caused performance issues if I tried to scrape it all at once when the app is loaded. Instead, I chose to scrape the categories at startup, but scrape the products in their respective categories when needed. This led to faster scraping times. Once the products for a certain category was stored, it no longer scraped for that category.

With the way the website is setup, each product style had its own available sizes. I figured the best way to store this data is by giving my product styles array which stores hashes. Each hash stored a key/value pair of the style itself and an array of sizes available, as well as the product link for that style.

```
style = {
  prod.css("div.product-style").text.to_sym => sizes,
  :link => link
  }
```

The tricky part of doing it this way was accessing the sizes when it was needed:

```product.styles.find{|a|a.keys[0] == style}[style][CLI.to_index(input)]```

In order to retrieve the specific size the user wanted, the program needed to first iterate over the product's `styles` array of hashes and find the hash that contained the specific style. It then needed to access the array of sizes, which was stored as a value in the style key. Once it retrieved the array, it selected the appropriate size based on user input.

Coding the logic of the app was pretty straightforward, the only other obstacle I ran into was working on handling edge cases where user input was invalid.

## The App

The app is simple, it welcomes you and lists the categories of products Supreme sells. To navigate much of the app, the user inputs a numbered selection correlating to what is displayed on screen. The shopping flow of the app is as follows:

1. User selects a category they want to shop for products in
2. Product list for the category is displayed, and user selects a product
3. Available styles (colors) for the product is displayed, and user selects a product
4. Available styles for the specific product/style combo is displayed, and user selects a size.
5. The cart total is displayed and asks if the user wants to continue shopping or checkout.

## Lessons Learned

The biggest lesson learned and time-saver for me was creating a flow chart prior to starting any coding. This made me think really hard on how to set up my design and figure out what needed to be worked on first. Of course, I ended up deviating from the flow chart I made but it helped immensely when starting from scratch.

I've also learned (and am still learning) how to search and read documentation effectively to get the information I need. 

## Summary

Overall, this project was a tough one just based on the sheer amount of scraping I had to do. I decided to go deeper than one level which made writing my scraping methods and accessing the data a little more complex. However, I've gotten a deeper understanding of OOP thanks to the difficulty of this project.

