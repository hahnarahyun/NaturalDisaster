# NaturalDisaster

In this project, we aim to predict property damage due to thunderstorm winds in Texas using shallow (one and two hidden layer) neural networks. Our method is heavily based on: https://arxiv.org/abs/1807.03456 

Storm Events Database (NOAA)
---
We downloaded the top 500 most damaging thunderstorms from the Storm Events Database from the National Oceanic and Atmospheric Administration. Due to missing values in the features we wanted to use as inputs, we ended up with a total of 353 data points. 

US Census Data
---
Coming soon

Input Feautures
---
The initial features we used were time, magnitude of the storm, damage to crops, begin latitude, begin longitude, end latitude, and longitude. We both trained a one hidden layer and a two hidden layer neural net on these features, and got a lowest MSE over a 100 iterations of 0.01. Later we added the mean income per county in Texas which improved the prediction accuracy of our model to a MSE of 0.00463. 

Important Notes
---
1. Our models are conditional models, meaning they assume that property damage WILL occur. This was the same approach as done by https://arxiv.org/abs/1807.03456 
