---
title: "Comparision of Factor Importance"
date: 2022-12-18
published: true
tags: [dataviz, hvplot, holoviews]
excerpt: "What are the factors contributed to the ridership increase?"
hv-loader:
  hv-chart-1: ["charts/Factor_Importance_2022_1.html", "500"] # second argument is the height
  hv-chart-2: ["charts/Factor_Importance_2022_2.html", "500"]
  hv-chart-3: ["charts/Factor_Importance_2019.html", "500"]

toc: true
toc_sticky: true
read_time: true
---

## 4.1 Introduction 

In this section, we are going to run three models. In the previous analysis, we hypothesized the ridership increase during orange line shutdown could be due to 1) increased trip from original orange line commuters now replaced by bikeshare and 2) ridership of low income neighborhoods. Thus we want to see how these affect the bikeshare demand. 

**The variable connected to reason (1) is nearest distance to orange line and to (2) is poverty rate in which the station is in census tract.**

We will first split the training set and testing set within the 2022 data points, then train the training dataset on variables that are similar to model part 1 and test it on the testing sets. 

Second, we will train the dataset on variables similar to model part 1 plus the two new orange line shutdown related variables, and run the model again on the train and test sets. This will give us an idea if the model can be improved with the added orange line shutdown related variables.

Third, we will run the variables, including the orange line shutdown related variables, on 2019 data, to see if the orange line shutdown factor importance would drop in 2019. 2019 data is chosen because 1) it has a similar average station monthly ridership to 2022 and 2) it reflect the bikeshare service pre covid. We can also see what effects covid might possibly cast on bluebike ridership.

The regression we chose here is **random forest**, which shows a high degree of accuracy.

## 4.2 Model without orange line shutdown related variables

<div id="hv-chart-1"></div>

The model showed an **accuracy (r2 score) of 91.11**. This shows the random forest model is very good at predicting bikeshare demand even without orange line related variables. 

Look at the importance, we see that the percentage walking to work (bsaed on 5-year acs 2020) in the census tract where the station is located in contributed the most to the accuracy of the model, followed by percent of employees, and lagge mean distance to the nearest five bikeshare stations. This could imply that people who commute to work by walking, are also likely to use bikeshare service to replace the walkable distance. This also could show that most people use bikeshare to work. 

Interesting percentage driving to work is the fourth. This is understanble, because post covid, most people started work remotely, especially for those who drive to work (imply a longer commuting distance). With the drop of population who used to drive to work, the number of bikers could increase if the residents are now using bikehare for shorter trips to go to a nearer grocery store for goods that would otherwise done in the car. 

Distance to Subway makes sense to be on the fifth, because bikeshare most of the time would fulfill the last-mile demand for transit riders.

## 4.3 Model with orange line shudown related variables

<div id="hv-chart-2"></div>

Model sightly increased its **accuracy to 91.13**, a 0.02 increase from the previous model when orange line related variables are added. 

The factors importance mostly related similar to the previous model. Distance to the nearest orange line station demonstrated some importance, placed on the 7th, its importance is similar to the distance to the nearest subway station, meaning that the ridership is not too much as related to orange line stations specifically, but the stations in the entire subway system. **This shows that free bikeshare benefited not only orange commuters, but also other subway commuters as well, most likely for last-mile coonecting demand.**

Poverty rate, on the other hand, performs poorly as a variable in contributing to the accuracy.

## 4.4 Model on 2019 data

<div id="hv-chart-3"></div>

The factors importance in 2020 is different from 2022. While percentage walking to work remains as the most important factor, percent biking to work, and percent white population have much higher importance in predicting 2019 ridership. This means back in 2019, people who commuted by biking were using bikeshare service for the trips, predominently white population. This makes senes, because there has always been a cultural stigma that bikeshare service and infrastructure incur gentrification in low, minority dominated neighborhoods. 

Distance to the nearest Station is still high at the 6th place. The importance for percent employees dropped, this could mean that in 2019, there is a greater amount of bikeshare trips for leisure purposes rather than commuting purposes. This is also backed by the increasd importance of distance attraction sites in 2019 and distance to the nearest orange line station (southwest corridor is right next by, a beautiful separated bike lane). 

Poverty rate remains low on importance, not as high as expected. 
