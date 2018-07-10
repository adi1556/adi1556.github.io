---
layout: post
title: MTA Traffic Analysis
---


-----



### Problem Statement

A non-profit company WomenTechWomenYes wants to hold their annual gala at the starting of the summer. They want to maximize the involvement of women in technology to attend the event to build awareness and reach as well as fill their event space. They want to use their street teams to reach out to their target populace on the entrance of MTA stations and collecting their emails. These people will then be sent free tickets to the gala.  

### Approach

WTWY is resource conscious and asked us to use MTA traffic data and come up with an analytic approach to answer the problem. In our opinion, barely using the MTA traffic data will not disclose the full extent of our reach to the target populace. We decided to use Foursquare data available online to come up with Points of Interests that target populace might be interested in and around the stations with the highest traffic. 

### Analysis

We downloaded the data from MTA's site from April 2018 till June 2018. 

### Data Cleaning:

* There was no unique identifier for a specific turnstile and hence we used Control Area name, remote unit ID station, SCP(specific address for a given device) and Station to come up with a unique identifier
* The values were cumulative over time and hence we aggregated the data using the difference of maximum and minimum value to get turnstile entries for every day per station 
* We are focusing on the time frame between 12.00 p.m. till 9.00 p.m as we think that will get us the bulk of our target populace who might be interested in signing up for the gala
* We checked stations which were getting a lot of entries of passengers on just one day of the week and considered it an outlier, changed the values with the mean of all entries to maintain a uniform distribution
* There were certain weeks where the number of days for which data was recorded was lesser than 7 and we removed those records
* Also, got rid of weeks on which recorded traffic was way off and wasn't humanly possible


*Steps after cleaning*: Aggregated data and were able to get weekly data through a turnstile per station

We were able to see that 3.7% of the stations were responsible for 22.3% of the total people going through turnstiles. We shortlisted top 10 stations by traffic to do our further analysis. Top 10 stations were spread across Central Manhattan as was expected.

![Image test]({{ site.url }}/images/BarPlotBenson.png)


### Adding Foursquare Data to MTA Data

A lot of traffic doesn't necessitate that people are interested in your cause. We wanted to target most of our workforce where we might find potential populace who might be interested in attending the gala. We focused on affluent women as they tend to be more open to the cause of WTWY. We shortlisted potential points of interest(POI) from Foursquare check-in data. Using Euclidean distance POIs were defined in a radius of 1 mile of each station. 

### Ranking Based on Resource Allocation Scheme 

Stations were ranked initially based on entries through each turnstile. When we ranked the stations on basis of nearby POIs, ranking changed drastically. We wanted both of these features in our final resource allocation scheme. We calculated percentages of each feature; % of entries through a station per week and percentage of POIs nearby a station. We took arithmetic mean of both of these features to come up with a metric which can be used for resource allocation towards stations. 

![alt_text](http://zwmiller.com/projects/images/monte_carlo/part5/business_impact.png)

| Table | filled | here |
| ----- | ------ | ---- |
| Value | value  | value|



### Final Recommendation     

We recommend that resources be allocated to each station using the scheme discussed above. It'll capture the target populace in areas they frequent for things they love. Happy emotions harbor the tendency to be nice to others. In our opinion, it will be easier to ask them for their emails.

### Future Work

* Refine POIs
* Donor list
* Break time in chunks


