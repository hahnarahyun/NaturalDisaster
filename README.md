# NaturalDisaster

In this project, we aim to predict property damage due to thunderstorm winds in Texas using shallow (one and two hidden layer) neural networks. Our method is heavily based on: https://arxiv.org/abs/1807.03456. Part of our code uses, adds to, and adjusts the methods used here https://github.com/jdiaz4302/tornadoesr. 

Storm Events Database (NOAA)
---
We downloaded the top 500 most damaging thunderstorms from the Storm Events Database from the National Oceanic and Atmospheric Administration. Due to missing values in the features we wanted to use as inputs, we ended up with a total of 353 data points. Also note that for missing values for latitude and longitude, we filled these in manually by looking up the latitude and longitude of the county these storms occurred in. We also filled in some wrong/missing values for the magnitude of the thunderstorm, but this was harder to find and thus did not give us many extra data points to include.  

US Census Data
---
Coming soon

Input Feautures
---
The initial features we used were time, magnitude of the storm, damage to crops, begin latitude, begin longitude, end latitude, and longitude. We both trained a one hidden layer and a two hidden layer neural net on these features, and got a lowest MSE over a 100 iterations of ?. Later we added the mean income per county in Texas and the "storm order" by county, which is a counter of how many storms have already occurred in this county. The underlying idea is that counties that see more and more storms would be better prepared. We find that adding these two metrics gives us a minimum MSE of 0.535. 

We also identified features that we could not include this time due to their unavailability but that could provide very useful insight into property damage done. Such features include county spending on infrastructure and change in wind direction.  

Important Notes
---
1. Our models are conditional models, meaning they assume that property damage WILL occur. This was the same approach as done by https://arxiv.org/abs/1807.03456. However, we did not include a binary classifier that decided whether or not a storm would cause damage, and therefore we omitted all zero entries for property damage. 
