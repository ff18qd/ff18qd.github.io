---
layout: post
title:      "Rails Portfolio Project"
date:       2018-01-27 22:40:18 +0000
permalink:  rails_portfolio_project
---


Rails session is the largest one in the program. It covers so many contents that in this project I have to go back and forth to previous classes and google online in order to get my bugs fixed. I still have one issue not fixed but would like to share some of debugging experience.

There is one requirement asking to display the error messages to the view page. For example, when user login with wrong user name and password or user sign up but with invalid user name or password, system won't allow user to do so and it is convenient to give user some hint of what they have done wrong. 

My problem is I can trigger the error messages because I put binding.pry and run rails console to see what error messages give me. But I can not see the error messages shown up in the view page. It is very tedious error but I think it is important to know every command what it does so that I can use correct command. I used redirect_to to show the view page, but this will lose the variable and error messages from that variable. Render is the correct method(action) to use in this scenario, the variable will be kept to the view page and hince the error messages can be listed. Render will not reload the page but redirect_to will.
