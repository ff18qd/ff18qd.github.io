---
layout: post
title:      "How to avoid CORS using AWS Cloud 9"
date:       2018-05-24 20:03:13 +0000
permalink:  how_to_avoid_cors_using_aws_cloud_9
---


Considering final project, technically there are a lot of contents to cover. It has the most vague description among all the portfolio projects. After reading the requirements, it seems I know what to do but where should I start? Don't worry, you are not the only one feel like this way. 

As you have done all the hard work, late nights studying, you can do it. This project is about using Rails backend and react-redux frontend. The first thing to make sure is that Rails and react can talk to each other which means React can send fetch request to get update and delete data from Rails backend(CRUD). It is not very complicated settings for people using VB, but it gave me A LOT of troubles and I am using AWS Cloud 9. I will put the link here for anybody may use Cloud 9 and could come for reference. 

https://docs.aws.amazon.com/cloud9/latest/user-guide/app-preview.htmls

Before this project when I run `rails server` or `npm start` I use preview url given by Cloud 9 to open the app in the browser. But preveiw url with different ports won't talk to each other due to corss-origin request sharing issue. It will throw an cross origin error when fetch request requesting data from Rails. Most platforms can use CORS gem and configure package.json to solve this issue if you are using localhost:port. In the document follow all the steps and read carefully( I did configuration once but didn't follow all the steps ... don't do that) configure security group and save the private ip and public DNS for later usage. All the configuration needs be done under root account. Then start the service from rails using private ip given by Cloud 9. Use public DNS and diffrenciate rails and react service by port. For example, 8080 is the default port which server start first will take this port and the other service has to use 8081 ect, unless you define the port within the start server command line. The public DNS changes each time the instance starts. Now you are all good to go with AWS Cloud 9. 

I had couple of coaches and friends help me figure out how to use Cloud 9 to make cross-origin resource sharing happen. Here would like to thank them all and especially Dakota and Janusz.  

*My 2 cents for final project or the coding journey is never to lose hope, if things don't make sense for you the first time, try 2nd time and 3rd time ect. till you get it. Happy coding!*

