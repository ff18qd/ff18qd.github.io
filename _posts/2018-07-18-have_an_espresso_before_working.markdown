---
layout: post
title:      "Have an Espresso before working"
date:       2018-07-18 12:21:37 -0400
permalink:  have_an_espresso_before_working
---


Espresso, a good idea in the moring. Um, I am talking about Android automation tool. I have heard of it before last week but never really thought about it until a job opportunity offered me a challenge to write some Espresso test code for them. 

The product is an Android App you can think of it similar like Uber or Lyft. The task sounds not too complicated. But trust me, when I made my hands dirty I know how many challenges I had. 

First install local environment of Android studio and run the source code. I don't have an Android phone so I need to install and use emulator to run the code. Make sure to use the same or above version of Android on seleted emulator otherwise emulator won't work properly. I suggest use the exactly the same version in my case I first downloaded version 28 other than requirement of version 27. And it turned out version 28 emulator didn't work well. So I rolled back to v 27.  

Play around with emulator to get familiar of what this app is about and how the functions work. I don't have Android development experience it is a bit hard for me to pick up in short time to read source code then get started. In order to meet the deadline originally a week but as QA lead would be on vacation my deadline was within 4 days. I had to find an efficient way to find out the solution. I played with emulator and app. And I get a clear idea of what the test steps were. 

Login the app, 
Input search content,
Click on the 2nd item in the searching result list,
On the driver's profile page, click on Call button

Lean the Espresoo. I found some good articles(blogs) and Youtube resource from this here, [http://www.qaautomated.com/p/blog-page.html](http://www.qaautomated.com/p/blog-page.html). The Android Development document is also very helpful[https://developer.android.com/training/testing/ui-testing/espresso-testing](https://developer.android.com/training/testing/ui-testing/espresso-testing).

The basic idea is to use id or text content (of course there are more other advanced ways) to find the element on the app and perform a behavior like click or input something then do an assertion on the action. To find out the id or the text name of the app element is from Layout folder inside the res folder. Android studio provides the ability to manipulate the layout. 

Step three is an autofull textbox task so need to use inRoot() and decor View to select a window inside a Main activity window. Here is a very helpful resource [http://www.qaautomated.com/2016/10/how-to-test-autocomplete-text-box-with.html](http://www.qaautomated.com/2016/10/how-to-test-autocomplete-text-box-with.html). 

The app will be not the current open app when user click on the dial call button. User will be in the Android call function page. The hard question here is if I run my test case and the test case ends successfully at this point. Next time running the test it will start from the Login step and Login will fail cause it is never logged out. I have tried some ways to use instrument registry to popup the lasted used app activity and tried to logout before test ends. But it wasn't successful. I made it another way around. To check the login page before my first step in the test script. If it is not Loggedout in the beginning I will fail the test case. It is a work around not the best approach. If I have more time I will find out how to log out and make it in the tear down part of the test. 

The final task of this take home is deployment! Yes deploy it on cricleCI. Here is my project [https://circleci.com/gh/ff18qd/AndroidDemo/13](https://circleci.com/gh/ff18qd/AndroidDemo/13). Well I have tried a lot of times it is a long story. Look closely the demo how their folder layout and follow strictly. It is my first time to use circleCI and I would recommend if you have a strict deadline and you are not an expert yet. Make it work rather than being panic about it. I used an extra folder first outside of my Andriod Demo folder so I failed in a couple of times to deploy. After I figure it out I deleted my old repo on Github and created a new one. Then comes the fight with config.xml. The sample yml file on the tutorial is not with the correct content I searched for other users questions in circleCI community and found they used yml specially for Android and I made changes but stuck again on download dependencies. 

It said gradlew permission denied. Community is helpful. Thanks for people who ask questions and posted the solutions there. I need to change gradlew read only to read and write. Make this permission change on local repo and do a git commit and push it to remote repo. Because circleCI is connected with Github remote repo not my local repo. I have to make this change in remote repo so that circleCI can access gradlew file on my Github. The deployment takes about 5 - 10 mins and all buttons are green!!!  

I am proud of myself to take the challenge and look out asking help and questions on different resources and made the deadline. Here is my Github too [https://github.com/ff18qd/AndroidDemo](https://github.com/ff18qd/AndroidDemo). My hands on experience of Espresso and circleCI are under my belt. 

