# NaturalDisaster

In this project, we aim to predict property damage due to thunderstorm winds in Texas using shallow (one and two hidden layer) neural networks. Our method is heavily based on: https://arxiv.org/abs/1807.03456. Part of our code uses, adds to, and adjusts the methods used here https://github.com/jdiaz4302/tornadoesr. 

Storm Events Database (NOAA)
---
We downloaded the top 500 most damaging thunderstorms from the Storm Events Database from the National Oceanic and Atmospheric Administration. Due to missing values in the features we wanted to use as inputs, we ended up with a total of 353 data points. Also note that for missing values for latitude and longitude, we filled these in manually by looking up the latitude and longitude of the county these storms occurred in. We also filled in some wrong/missing values for the magnitude of the thunderstorm, but this was harder to find and thus did not give us many extra data points to include.  

US Census Data
---
We used a combination of the U.S. Census Bureau’s American Community Survey 5-Year Estimates from 2009-2017 and the U.S. Census Bureau’s 1990 and 2000 decennial US census data to get each county's mean household income during each storm event. For events that transpired between 2009 and 2018, we used the 5-Year Estimates (the values changed each year, but were based on data from the past 5 years of surveys) as the data better represented yearly trends. For events that happened in 2018 we used the data from 2017 as the 2018 numbers are not available at this time. For events that happened before 2009, we used the decennial census and used the closest year's data (1990, 2000, or 2009) as yearly estimates were not available that far back.

Input Feautures
---
The initial features we used were time, magnitude of the storm, damage to crops, begin latitude, begin longitude, end latitude, and longitude. We both trained a one hidden layer and a two hidden layer neural net on these features, and got a lowest MSE over a 100 iterations of ?. Later we added the mean income per county in Texas and the "storm order" by county, which is a counter of how many storms have already occurred in this county. The underlying idea is that counties that see more and more storms would be better prepared. We find that adding these two metrics gives us a minimum MSE of 0.535. 

We also identified features that we could not include this time due to their unavailability but that could provide very useful insight into property damage done. Such features include county spending on infrastructure and change in wind direction.  

How to run the code
---
The code is split up into two files: texas_pure_thunder.ipynb and texas_thunder_augmented.ipynb. Both files can be run from first to last cell to show the results we have in the report. The rest of the repository consists of data files we used to perform our experiments. 

Important Notes
---
1. Our models are conditional models, meaning they assume that property damage WILL occur. This was the same approach as done by https://arxiv.org/abs/1807.03456. However, we did not include a binary classifier that decided whether or not a storm would cause damage, and therefore we omitted all zero entries for property damage. 
