---
title: "Introduction"
date: 2022-12-20
published: true
tags: [dataviz, matplotlib]
excerpt: "Project description"
toc: true
toc_sticky: true
read_time: true
---
## Background

On August 18, 2022, the Boston MBTA’s Orange Line was shut down for a month due to safety repair work. To open more transportation options for Orange Line commuters, Mayor Wu announced that Bluebikes, Boston’s bikeshare system, would be free during the month of the shutdown. During the month, bikeshare demand surged tremendously, bypassing expectations of demand even for the free period. Monthly ridership has increased by over 100,000 in August and September in 2022, a growth of nearly 40% from the previous year. 

## Research Question

Essentially, this project explores the effect of orange line shutdown and free bikeshare service on ridership. To see effects, the following questions are answered: 

* What new trend did we see during the shutdown period?
- What areas' riderships have been impacted the most by the orange line shutdown and the free bikeshare service?
- After Bikeshare became free, what variables contributed ot the increase in demand?

## Method

To build our model, we decided to integrate a variety of facilities as spatial variables through calculating the distance from Bluebike stations to certain amenities. From the MBTA or City of Boston open data websites, we drew rapid transit stations, colleges and universities, high schools (as high school students can viably use Bluebikes), and open space. Roads and tourist attractions were taken from OpenStreetMap using the *osmnx* package; to narrow the wide variety of tourist attractions, we only used those that are also labeled "historic." 

For all data, the log of the average mean distance was taken. For any data that came originally as points, we read data in using *geopandas* calculated the distances from every Bluebike station to the nearest point. For line data, such as roads or the bike network, it was transformed into points through finding the nodes on each; this may have resulted in slightly larger distances for Bluebike stations next to less curvy bike lanes, but was effective enough for our model. Lastly, centroids were used for open space polygons; this may have had a similar effect of larger distances for very large parks.

Additionally, we utilized census data, such as population density, income, poverty rate, car ownership, commuting patterns, and percentage of white residents to further strengthen our model. This was created outside of our code, then read in using *geopandas*.

We also wrangled added lag station distance:

* The lag bluebike station distance is based on year, because bluebike stations kept expanding across the years, resulting in differnt number of stations every year. We first gathered the station data from bluebike website, and filter out all exsiting stations of that year and break them a part into different dataframe. For example, for 2019 station data, it will be all stations constructed before 2019, which is "Deployment Year" <= 2019. 
- We run nearest neighbor to find the distance of the five nearest bluebike stations, and take mean of the distance, then log it for equal distribution.

And lag ridership:

* Lag ridership should be based on month and year, since bluebike ridership varies on seasons and time. To get the ridership, we first split the dataset based on year and month, then we get geometry of each station in that year. Note that some of the stations might not have records during in a month, resulting in an index error. Because of this issue, we have to expand the monthly data to have all the stations that have records in that year. For exmaple, in July 2018, only 177 stations have records out of 213 stations used in 2018. We have to expand the rows in July to have 213 stations, and mark those that have no records with a ridership of 0. 
- We make the station id (which is unique) as the index, and get the mean of ridership of the nearest 5 neighbors. Finally we rejoin them back to the splited year-month datasets, and append them together at the end. 
- Note that because of the slight difference in station names across the yera, the number of objects of the new datasets are different from the original dataset generated from the current station data on bluebike website.

Our analysis is based on random forest regression as it shows a degree of high accuracy. 