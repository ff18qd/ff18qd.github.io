---
layout: post
title:      "Sinatra Portfolio Project"
date:       2017-12-16 22:10:07 +0000
permalink:  sinatra_portfolio_project
---


While doing the sinatra portfolio project from scratch, I picked up some knowledge that I already forgot. All the previous Sinatra labs are cloned and forked and they all have setup structures. So I don't need to worry too much about exactly which part works for what. But in portfolio project, the idea and structure are all from me. 

The first thing I forgot is why has_secured_password not working. I have created a column named password for my users table. But it can not recognize the password column. It asked me to check the column name. Then I went back to previous class and found that I need to change the column name to password_digest instead of password. Although in params the key is still called password but in the table it is named as password_digest.

Second thing is to set session_secret for secured password. Otherwise user cannot really logged in, the session cannot record the user id.

Third is why I cannot see my coded view page. It worked for previous labs, exactly the same code. But why not working in portfolio project? Well, the layout page needs to be filled with basic HTML structure so that the views can be displayed correctly in the browser.

Learn, practice, forget and learn again. 

