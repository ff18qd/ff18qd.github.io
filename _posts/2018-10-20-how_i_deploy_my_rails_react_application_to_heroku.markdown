---
layout: post
title:      "How I deploy my Rails React application to Heroku"
date:       2018-10-20 23:21:04 +0000
permalink:  how_i_deploy_my_rails_react_application_to_heroku
---


It has been a while after I completed my final project which I also put as my major portfolio project - Rails backend and React Redux frontend. I have heard some of my peers have deployed their application to Heroku. I also heard that it caused some troubles for them to troubleshoot their particular issues. As I started my job hunting right after graduation I got small take homes(sometimes not that small) I didn't have much time in investing to deployment. But as I read the job requirement from different companies, quite of them have mentioned Heroku in the skillset. 

I want to take Heroku under my belt and as the first step I want to deploy my final project on to it. Another reason I want to do it fast casue my free AWS Cloud9 IDE would expire soon :) 

Day 1 - read through some blogs 
[blog about deploying Rails React app to Heroku](http://alexandrawright.net/posts/deploying_a_react_app_with_rails_api_to_heroku) and [blog about how to solve cors issue using foreman gem](https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/).
Register on Heroku and download the Heroku CLI to AWS C9 using npm. Configured `heroku login` to my local repo. Heroku CLI works with node v8 + so I did a node upgrade from v6 to v8. On day 3 I found heroku command line doesn't work because the default node version is set as v6 in my AWS Cloud9. I changed the default version of node to v8 then heroku command line works again. whew

Day 2 - make changes to Gemfile, Rakefile ect according to the two blogs mentioned above. 
I met some issues today, some solved some not. 
If your Heroku is heroku-18 it doesn't support Ruby 2.3 so upgrade ruby version to 2.5.1 or any version which is up to date. 
I work on a branch not master in my local repo but heroku would skip any deployment if user try to push to a non master branch to Heroku. Use the command git push heroku yourbranchname:master` instead of `git push heroku master`

Problem unsolved: Heroku runs `$ bundle exec rake -P` under the root directory. My rails api is in a folder under root directory. When I run this command manually under the folder path it can be executed without error but Heroku can't find the rake tasks, because rails api is not in the root directory.

I plan to solve it to reorganize my folder layout of local repo. Move every Rails stuff out to the root directory but leave React app in a secondary folder. 

I got another reference from an alumni [more details included from the start of setup heroku, rails and react](https://medium.com/@bruno_boehm/reactjs-ruby-on-rails-api-heroku-app-2645c93f0814)

Day3 - Following Day 2's assumption I changed my folder structure and layout. I took out all contents in my nextstop-api folder to the root directory and put nextstop-client folder in the secondary directory. This helped solve the rails app deployment error in Day 2. 

I have my heroku app url and the react frontend is displayed well. 

New issue, fetch from the rails backend failed due to ```GET https://agile-brushlands-22848.herokuapp.com/api/nextstops 500 (Internal Server Error)``` . The backend route doesn't work properly, url/api/nextstops doesn't lead to anywhere. 

Thanks Temi who helped me troubleshooting on a Friday night. She graduated mid of Sep and she had her app deployed successfully on Heroku. 

Expecting Day 4 for some progress.

Day 4 - I was thinking the Heroku may not allow user to reach rails backend so I posted my question in Slack. johnfewell said he could open the rails backend json file link as what we did in local env and there was no 500 internal error. My assumption was wrong. He asked me to check the heroku logs. In the heroku logs it said it couldn't find the relation of my database and there is no table. It is database issue. I reset the heroku postgresql and did a migration `heroku pg:reset` `heroku run db:migrate`. This solved the database not setup correctly issue. I can successfully create the form and persist it to the backend. 

This step is also mentioned in the third blog link above. Don't miss any steps when deploying. 

Now it is Heroku time [nextstop](https://agile-brushlands-22848.herokuapp.com/).

![](https://www.westelm.com/weimgs/ab/images/wcm/products/201824/0075/brass-word-object-cheers-c.jpg)
