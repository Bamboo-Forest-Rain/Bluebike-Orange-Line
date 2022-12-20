---
title: "Limitation"
date: 2022-12-17
published: true
tags: [dataviz, matplotlib]
excerpt: "Project description"
toc: false
toc_sticky: true
read_time: true
---

## Limitation 

We do want to recognize the limitation of these models. The biggest one is the demongraphic and social-econoimc data that is from 2020 5-year ACS. We decide to use this 2020 5 year ACS, because 2021 1 year ACS is unrealiable due to COVID. This could lead to the result difference in 2019 and 2022, as 2019 result looks more reasonably than the one in 2022 -- percent biking to work is highly correlate dwith increase in bikeshare deamnd. 2020 ACS is mostly complied with data pre-COVID, and is more reflective of the situation in 2019 than 2022, when the work life, commuting patterns are drastically different. We could only make educated guesses on what could possibly happen, but not exactly certain of how these factors could impact bikeshare demand.

Second, poverty rate remains as an unimportant factor is understandable. Because places with high poverty rate do not use bikeshare as often as other places with low-poverty rate, and not enough data points could be collected for them. A better way to show how poverty rate plays into this free bikeshare period, is to compare it with the growth of ridership, instead of just looking at the number of ridership. Perhaps, places with high poverty rate shows great growth in ridership during free month compare to other places where ridership has always been high. 

Third, Bluebike data is not collected completely. We noticed that after 2019, most of the age, zipcode, and gender information is either missing or unrealiable. Originally we decided to look at pattern changes in users' demongraphic data as well, but had to forgo the idea because of the missing and inaccurate datasets.