---
title: "Exploratory Analysis - Changes in Trend"
date: 2022-12-19
published: true
tags: [dataviz, hvplot, holoviews]
excerpt: "How did orange line shutdown contributed changed the travel pattern during the time?"
hv-loader:
  hv-chart-1: ["charts/ridership_line.html", "500"] # second argument is the height
  hv-chart-2: ["charts/stacked_bar_usertype.html", "400"]
  hv-chart-3: ["charts/averagestationridership.html", "650"]
  hv-chart-4: ["charts/map.html", "800"]

toc: true
toc_sticky: false
read_time: true
---

## 1. Looking at the Trend prior and during Orange Line Shutdown

We will compare monthly data for the month of July, August, September between 2018 and 2022. We recognize that ridership is affected by the number of newly constructed stations, and we will further divide monthly ridership by the number of stations constructed that year. For example, after we aggregated the overall ridership for the month of July in 2018, we will devide the number by the number of stations in 2018 to get ridership per station of that month. 

Ridership in this case is defined by the pickup rate at the start station.

### 1.1 Ridership

<div id="hv-chart-1"></div>

The graph shows the average station ridership in the month of July, August, and September. Colored lines reporesent different years. We see that in 2020, the ridership is greatly hit by COVID-19. In 2021, the ridership started to recover, but still not yet returned to pre-COVD level. However, we see a great increase in the ridership in summer 2022. The increase rate, too, is much faster than other years, especially between the month of August and September. This is most likely due to orange line shutdown, when most orange line commuters began to replace their subway trips with bikeshare trips. Note that South west corridor has a really nice separated bike lane, going parallel to the orange line, this could be a factor in ridership increase as well. 

At the same time, some low-income residents no longer have financial barrier to use the bikes (requires a credit card and a hold of $25), they perhaps also contributed to this increase.

### 1.2 Membership

Bluebike has two type of users: 1. Subscriber - who has signed up for monthly or annual rider pass 2. Costomer - who just used the bike for once. We want to see how the membership has changed during the years as well. During orange line shutdown, one is required to sign-up and become a subscriber to be a free bikeshare user. We will present the data as user type in percentage of that year, as well as avaerge station number of subscriber and customer per month per year.

<div id="hv-chart-2"></div>

Red bars represent percent subscribers and Blue bars represent percent customers. Subscribers are always more than customers, meaning that most likely Boston and nearby city residents are using the service more than visitors who are more likely to use the service. Customers are usually around 20% - 30% and subscribers 70% - 80% of the users. In 2021 and 2022, the percentage of subscribers slightly decreased, perhaps residents at the time started to work remontely even during the summer days. 

The trend in 2022 is interesting, as tourism started to resume, we would suspect that the percentage of customers increases. Instead, the percentage of subscribers kept increasing. For the first time in five years, the percent of customers dropped to 10%. 

As more people started to be aware they could sign-up for free membership in August to September 2022, perhaps even some of the tourists begin to register for the free service, thus we see a bug drop in number customers. 

### 1.3 Overall membership and ridership trend

<div id="hv-chart-3"></div>

When we look at the overall trend of average station membership, we indeed saw a dramatic decrease in subsctibers in summer 2020 comparing to summers of the other years due to COVID.  In summer 2021, the number of subscribers resumed to the level in summer 2019 (especially comparing the September data). In 2022, we see a huge jump up in subscribers, exceeding the summer of other years. The increase rate is the fastest between August and September, shown by the steep slope, at the same time the number of customers decreased in a great extent. 
### 1.4 Spatial ridership change across each year and station

<div id="hv-chart-4"></div>

The map above shows the expansion of bikeshare service on census tract basis. Across the years, the maps follow some basic pattern:
    1. Boston downtown and Cambridge always have the highest ridership per station, due to its students and tourists population. 
    2. The more spread out from the center, the less the ridership per station

We see an interesting pattern in 2022, when Orange Line was shutdown and bikeshare service was made free. We see that colors changed very apprently across the month, especially in the south side (where majority of the low income neighborhood are at). Despite the ridership increase near the orange line, the ridership have also increased in other places away from the line. 

### 1.5 Conclusion

By looking at the trends, we definitely see the effect of free bikeshare service in August to September in 2022. We see that there is a huge spike in average station ridership, number of subscribers, and increase in ridership in low income neighborhoods. We see that not only the original orange line commuters and college students living along South west corridor benefited from the free program, even the low-income neighborhoods away from the orange line might also be benefited from it. 
