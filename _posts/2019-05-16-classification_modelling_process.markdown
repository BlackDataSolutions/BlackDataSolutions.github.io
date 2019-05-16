---
layout: post
title:      "Classification Modelling Process"
date:       2019-05-16 16:06:19 -0400
permalink:  classification_modelling_process
---


Here I'll discuss how I selected my models. The process was one that took me a good deal of time and involved a lot of review of looking "under the hood" of these algorithms. One of the things that I learned throughout this process is that it's relatively easy to actually run the models in python- it's really just a few lines of code.

However, if you don't understand what the algorithm is actually doing underneath it makes tuning the hyperparameters very difficult and extremely time consuming. When I first started my hyperparameter tuning, I ran into this problem several times and had to re-educate myself on what ranges of hyperparameters were best suited to each model and each classifier. Below, I've briefly outlined the process I followed for my model selection.

**Outline a problem, and more importantly: a goal**

* This is the most important step. Be sure not to select a goal that's too vague- in my experience the more specific you can get with your problem statement the better of you will be. I found it far easier to tune my model to specific problems instead of trying to broadly apply a model to several different problems. 
* Choose something that interests you. The thing that makes data science so exciting for me is that there is data virtually everywhere you look. If you don't choose something you're interested in that writing the code will be like walking through molassis. 
* Finally, use the data to help you choose a problem. It is often difficult to pick a problem and then go find data about it. It is far easier to find a dataset that interests you and brainstorm problems/goals that pertain to that data.

**Try baseline, unmodified models**

* There are dozens of classification and regression models out there. My approach was to first try all of them and compare them against each other without any tuning.
* What I was looking for when I did this was overfitting as evidenced by an obscenely high training accuracy score
* I compared the testing accuracy for each model to assess which were the best performing

**Use k-fold cross validation to assess the accuracy of each model for a variety of different train/test splits. **

* I found it extremely useful to use visualizations here and visualize the different mean 10-fold CV accuracies for each of the models. This gave me more comfort that the models I had selected using baseline analysis were right for the data

**Use hyperparameter tuning in the form of GridSearchCV**

* GridSearchCV is an incredibly powerful tool that can be used to test a grid of given hyperparameters for any given model. 
* I used gridsearch for each of my models and collected a list of the optimal parameters for each. I also took testing accuracy scores for each and compared them.

**Pick the best models and fit them on training data.**

* After using hyperparameter tuning to find the optimal parameters, split the data into training and testing sets so you can train your models and then test them on some data. Find out which model performs the best for your given data and perform additional hyperparemeter tuning if you want to.

**Analyze the results and use the model predictively**

* Once you have a model that can predict a classification correctly, you can feed in data to it and get expected classifications! 
