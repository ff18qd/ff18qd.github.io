---
layout: post
title:      "Address Validator a take home project"
date:       2018-07-14 20:35:32 +0000
permalink:  address_validator_a_take_home_project
---


I am actively looking for new jobs. I would like to record how I do my take home projects. Every project has its own challenge and I am learning and growing through this process.

I received a take home project which asked me to add some features for Ruby on Rails project. User input the address and click on validation button. The validation result will shown up. The form and database schema are provided and schema can't be changed. 

The big challenge I faced was the form has street_address, city, state and zip_code four inputs. But Address model has 12 columns here are some of the columns: 
* house_number, 
* street_name, 
* street_type, 
* street_predirection, 
* street_postdirection, 
* unit_number, 
* unit_type
The input street_address is a string but how to break it down and accurately fill in these columns? Some columns can be empty but house_number, street_name, city, state and zip code can not be empty. 

I can not change the schema nor change the form. So I tried to look for some gems helping me to break down the street_address. Haven't found any perticularly for this case so I decided to use some map API to make my own data with the columns that I need to match with. I choose to use geocode API. https://developers.arcgis.com/get-started/. 

The findAddressCandidates service can find any number of matched address from a single line of address and the geocode can break it down to more detailded address information. I selected 
* AddNum,
* StName,
* StType,
* StPreDir,
* StDir,
* UnitType,
* UnitName,
* City,
* RegionAbbr,
* Postal
to match with the Address model schema. 

But here comes another issue. findAddressCandidates can fill some missing part of address information automatically and it can correct some wrong input like if you input vague zipcode, geocode API can provide an accurate one. Thus when I persist data to database, my data is not the same as user's input they are processed by geocode API. In case the address user has input has 4 error fields, the alert might only show 2 errors cause geocode API corrected 2 of them automatically.

I haven't figured out another way to realize it yet. If you have any good ideas, please leave a message or contact me. I will be glad to hear from you.

My github: https://github.com/ff18qd/address-validator-master
