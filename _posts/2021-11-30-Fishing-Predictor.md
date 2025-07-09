---
layout: post
title: Fishing Predictor
subtitle: A Web App to Predict Fishing Activity of Vessels
image: https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/gfw-thumbnail.jpg
---

This web app predicts the fishing activity of Pole and Line vessels based on their position, speed, and the time of year. The data comes from Global Fishing Watch, a non-profit organization that uses data and scientific analysis to promote more sustainable fishing practices.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/map%20of%20fishing.png)



## Data Analysis and Feature Engineering

The dataset includes various features such as Longitude, Latitude, and Speed, which are used to predict the fishing activity of vessels.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Features.png)

Features such as speed, distance from port, longitude, and latitude were taken directly from the dataset. Additionally, the feature “Area” was created by calculating values based on longitude and latitude, and month was extracted from the timestamp data.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Area.png)

## Predictive Model

For prediction, we used a Random Forest Classifier model because it handles both numerical and categorical variables effectively.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Model.png)

## Model Accuracy and Precision

After running and testing the model, we found it achieved a 96% test accuracy, which is impressive. However, since the dataset was imbalanced, accuracy alone wasn’t a reliable metric. To get a better understanding, I also evaluated the model’s precision, recall, and F1 score—all of which scored above 90%, indicating strong overall performance.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Confusion%20Matrix.png)
![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Classification%20report.png)

## Web App

Finally, I created a web app hosted on Heroku that integrates the predictive model. Now, anyone with the necessary information can use the app to predict fishing activity.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Prediction%20page.png)


![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Fishing%20Predictor/Result.png)



## Future Plans for the Project

I’m really proud to have completed this entire project on my own. The app works exactly as planned, but I believe there’s always room to improve. Some of the future enhancements I’m considering include:

•	Tune the model’s parameters to improve accuracy and precision

•	Experiment with different predictive models

•	Develop and incorporate new features to enhance predictions


[Notebook and data](https://github.com/Ekram49/gfw)

[Web app](http://fishing-predictor.herokuapp.com/)

