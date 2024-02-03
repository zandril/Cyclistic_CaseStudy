# Cyclistic_CaseStudy
Introduction
In this case study a fictional bike-share company based out of Chicago called “Cyclistic” is looking to produce more annual memberships. To do this we must understand how casual riders and annual members use the bike-share differently. The goal from these insights is to design an innovative marketing strategy to convert casual riders into annual members. For this to be successful we must back up our recommendation with data insights and visualizations.

I will be looking at data for a company named Cyclistic which runs a bike sharing program in the Chicago area. The program currently has 5,800 bikes and 600 docking stations located around the city. The company has looked at its financial data and has determined that annual memberships are more profitable than casual riders. They are now looking to focus on converting casual riders to members.
For the company to do this we first need a better understanding of how the usage of the two groups compare. We will look for similarities and more importantly differences so that we can create a campaign to target casual riders.
The data provided to use can be found here we will be looking at the data from 2022 in its entirety to see how trends change over the course of the year. The data contains a few fields where each ride started, ended, the time the ride started and the time the ride ended as well as the stations the ride started and ended at.
Process

First we loaded the data into Excel to quickly look through and find issues with the data that we can fix now before adding the dataset to a SQL database. We cleared out rows that were missing information or if we could find that information and fill in the blanks.
We also checked formatting to make sure data input correctly. We did this via filters and cell formatting and using Trim to remove and spaces that could cause issues. After this the data added into BigQuery, Googles SQL platform based in the cloud. Here is a link to a few of the queries used [combining and transforming data.sql](https://github.com/zandril/Cyclistic_CaseStudy/blob/ede0df82360e50c7f7df847e4df0198c18d7671a/combining%20and%20transforming%20data.sql).
Below you can see the different fields available to be used in the analysis process.

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/72fb3054-d4bf-46ee-8f5b-e74cf70b9f8b)

Analyze 
Using Tableau we can look at different information the display here is static however a link to my profile will be included for a interactive dashboard

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/6eb0146a-7881-41d6-8cb0-4ca5db20b1da)

Over the course of 2022 Members made up around 60% of the total rides that year while casual riders made up around 40%. This alone tells us that there is a sizable number of riders using the service who do not have annual membership.
We also have the number of trips taken by each type of rider and frequency over the course of the year.

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/7cc8d074-ae94-43f9-a512-ed196cf96d79)

Like the pie chart we know members make up around 60% of the usage we can see however during the summer especially July they are virtually even. The distance between the two lines is the same throughout the year but in July we see that casual riders and members are neck and neck in usage.
The chart below shows the average trips per day of the week:

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/08722c3c-1c60-413f-a211-397481e848af)

We can see Sunday is where both members and casual riders have the same usage however on Saturday on average there are more casual riders out around the city compared to member riders.
In this last chart we will compare the ride duration of both types of riders

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/4ec69108-74e0-4699-b719-5e7384be3c6b)

We can see that throughout the entire year casual riders have their bikes rented for a longer duration compared to members.
These charts tell us that. 
1.	Riders who are members make up most riders. 
2.	In the summer both casual and members nearly have the same usage
3.	Sundays we see similar usage however on Saturday we generally see more casual riders.
4.	Casual riders average longer trip durations than members 
Because of the increased usage during the summer by casual riders we can make some inferences. The assumption is that most members use the bike for commuting to and from work and or home if they live in the area.
We can also infer that casual riders have longer the bikes out longer than members because they are making a day out around the city and so are making a few stops while they are out while members are not out as much compared to members on the weekend.
Next let’s look at the areas where most trips start and end: 

![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/20d36591-6bc9-487f-a44f-b3a0ca01c213)
![image](https://github.com/zandril/Cyclistic_CaseStudy/assets/41587782/106bbf16-028c-4959-b8f0-be48f678693b)

Casual riders tend to start their trip through major stations, so they are coming into the city and renting the bikes close to major subway and bus stations, most riders who are members begin their trip at a few similar stations as the casual riders but there a few large clusters located around or close to the downtown core. With that we can assume most members live in or remarkably close to the downtown core of the city and casual riders are located in the suburbs around Chicago. 
Many of the casual riders end their trips near their starting position or a major public transit location. While members end their trip in similar locations but also more dramatically spread around the cities.
With this we know that:
1.	Casual riders prefer using their bikes throughout the day especially during the summer and weekends.
2.	They rent their bikes on average much longer than a annual member
3.	Their journey usually ends around the coast and close to major public transport locations.
A link to an interactive dashboard with this information can be found here. This link will take you to my Tableau profile where you can look and play around with the data for a better understanding.
Recommendation 
I would like to bring forward a few recommendations:
1.	Summer should be a major focus for advertising there is a massive swing in the amount of casual riders during this time and if they can be showed the value of an annual membership especially if it can save them money we should be proactive in letting riders know.
2.	Since the summer and weekends are the most important days for casual riders we can even think about implementing seasonal or weekend passes. These passes will of course be cheaper than the annual pass. With the lower cost casual riders might be more open to a pass that suits their needs better. A casual rider may even decide to upgrade their membership.
3.	Stations near different attractions and the coast are where we should first push promotions since most of the casual riders can be found here.
I believe weekend and summer passes might be a fantastic way to bring a casual rider into the subscription. If they see the value in these programs they might decide to upgrade to an annual membership and increase their usage as well.
