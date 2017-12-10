---
layout: post
title:      "Playlister - A lab I think I can never fix"
date:       2017-12-10 22:41:19 +0000
permalink:  playlister_-_a_lab_i_think_i_can_never_fix
---


As the course becomes more complicated, each failed test contains much information and need to look into carefully and check several folders and files. 

Playlister takes me 4 nights to pass all the tests. I am working on part-time program. First I had issues with database setup, and had to remove the local repo and clone the repo again. This took a whole night includes try different ways to solve the database problems. I have tried out different way to drop and setup migration several times.

Everything seems passed quickly after that but then edit page cannot pass the one test. The show page couldn't find the song's name, but in the server everything seems good. I shared screen with three coaches. Once it was pretty close to the point, but we missed that and tried on other directions. In the last screenshare, I know what the issue was after tech coach explained why I get a nil for params[:genres] cause I didn't check it in the checkbox. So I saved but genres didn't get updated during the edit, params didn't save it either so it was nil.Then with a nil array, controller or edit view cannot patch correctly and test never get passed to show page. This is why it cannot find the song's name. 

The test is not speaking this part nor the course, but do check the checkbox if your song has those genres. 

This lab is the longest one that I passed except portofolio project so far. You don't know how many times I thought I could never figure out the problems and I could never pass the test. Is it the right thing that I am doing? I doubt myself a lot. But thankful I have so many tech coaches they are all trying so hard to find out the issue and try different ways to tackle it. The way to solve a problem is keeping on trying and thinking. 
