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

We were able to see that 3.7% of the stations were responsible for 22.3% of the total people going through turnstiles. 
![Image test]({{ site.url }}/images/BarPlotBenson.png)

![Image test]({{ site.url }}/images/8020.png)

We shortlisted top 10 stations by traffic to do our further analysis. Top 10 stations were spread across Central Manhattan as was expected.

![Image test]({{ site.url }}/images/Stations.png)


### Adding Foursquare Data to MTA Data

A lot of traffic doesn't necessitate that people are interested in your cause. We wanted to target most of our workforce where we might find potential populace who might be interested in attending the gala. We focused on affluent women as they tend to be more open to the cause of WTWY. We shortlisted potential points of interest(POI) from Foursquare check-in data. Using Euclidean distance POIs were defined in a radius of 1 mile of each station. 

![Image test]({{ site.url }}/images/StationEntries.png)

### Ranking Based on Resource Allocation Scheme 

Stations were ranked initially based on entries through each turnstile. When we ranked the stations on basis of nearby POIs, ranking changed drastically. We wanted both of these features in our final resource allocation scheme. We calculated percentages of each feature; % of entries through a station per week and percentage of POIs nearby a station. We took arithmetic mean of both of these features to come up with a metric which can be used for resource allocation towards stations. 

![Image test]({{ site.url }}/images/StationEntriesPOIs.png)

| Rank | Station | Combined % Total | 
| ----- | ------ | ---- |
| 1. | Penn Station - 34th St  | 13.60|
| 2. | Grand Central - 42nd St  | 13.03|
| 3. | Union Square - 14th St  | 12.80|
| 4. | Herald Square - 34th St  | 11.81|
| 5. | 23rd St and 5th Av  | 11.44|
| 6. | Times Square - 42nd St  | 10.06|
| 7. | Rockefeller - 47th-50th St  | 8.18|
| 8. | Columbus Circle - 59th St  | 7.16|
| 9. | Fulton St  | 6.45|
| 10. | Path WTC  | 5.42|


### Final Recommendation     

We recommend that resources be allocated to each station using the scheme discussed above. It'll capture the target populace in areas they frequent for things they love. Happy emotions harbor the tendency to be nice to others. In our opinion, it will be easier to ask them for their emails.

### Future Work

* A refined POIs list will get us a better understanding of people WTWY is targeting
* Getting a hold of previous donor list of WTWY will help us in targeting stations in neighborhoods where more potential donors live and work
* We can break down the entry traffic in smaller time periods to identify best times to send representatives to stations


