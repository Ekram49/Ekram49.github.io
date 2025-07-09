---
layout: post
title: Building a Web App to Predict Kickstarter Campaign Success
image: https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/kickstarter-logo.jpg
---
As a Lambda School data science student, I, along with my peers, was tasked with creating a web app to predict the success or failure of Kickstarter campaigns. It was a fun and rewarding project—building a fully functional, useful app from scratch in just four days felt amazing!

Investing in a Kickstarter campaign isn’t without risks. If a campaign fails, investors lose their money. That’s why it’s important to evaluate the likelihood of success before backing any project. Wouldn’t it be great if someone had a sixth sense for spotting winning campaigns?

Well, lucky for you, our app does exactly that.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/thinking.jpg)

We used data from [Web Robots](https://webrobots.io/kickstarter-datasets/), which provides comprehensive information on Kickstarter campaigns. This dataset gave us all the features needed to build a predictive model, empowering our app to forecast the success or failure of any given campaign based on its characteristics.

## The Features We Used to Create Our Model Were:

•	Category

•	Description Length

•	Campaign Goal (in USD)

•	Campaign Length (Days)

•	Staff Pick

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/feature%20importances.jpg)

## Exploring the Dataset, We Found That Out of 209,445 Kickstarter Campaigns:


•	121,651 campaigns were successful

•	73,683 campaigns failed

•	8,904 campaigns were cancelled

•	5,207 campaigns are still live

![creep](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/feature%state.jpg)

After further exploratory data analysis, we used a Random Forest Classifier to build our predictive model. It achieved approximately **75.3%** accuracy on the test data, which we were quite satisfied with—especially considering the many variables that can influence a campaign’s success, making a perfectly accurate model nearly impossible.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/app-1.jpg)

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/feature%20importances.jpg/app-2.jpg)

To make our predictive model accessible, we developed a [Flask app](https://ds-15-ks-2.herokuapp.com/ that lets you input your campaign’s features and outputs the probability of its success.

After spending significant time analyzing the data, building the model, and developing the app, we suggest that if you’re planning to start a Kickstarter campaign or invest in one, make sure to:

•	Set a reasonable campaign goal

•	Keep the campaign length short

•	Write a clear and compelling campaign description

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/Kickstarter/best-of-luck-picture-with-thumb.jpg)

## Credits:

•	Antonio Peterson - Project lead

•	Jace Hambrick - Data Engineer

•	Jashim Rashid - Data Engineer

•	Luis Urene - Machine Learning Engineer

•	Ekram Ahmed (Myself) - Machine Learning Engineer

## Resources:

•	[Github repo of the project](https://github.com/Build-Week-Kickstarter-Success-2/DS)

•	[Datasets](https://webrobots.io/kickstarter-datasets/)

•	[App](https://ds-15-ks-2.herokuapp.com/)
