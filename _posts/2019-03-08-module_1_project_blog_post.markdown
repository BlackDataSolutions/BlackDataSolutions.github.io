---
layout: post
title:      "Module 1 Project Blog Post"
date:       2019-03-08 16:58:59 +0000
permalink:  module_1_project_blog_post
---


As I began this project last weekend, I was feeling great. In a matter of hours after receiving access to the data, I had imported the data and began scrubbing it. This seemed like a cakewalk! When I began removing zeros and reformatting the data, I had very few issues and everything seemed to be working just like it had in the labs and readmes! After 3 weeks of working hard on labs and walkthroughs, I was beginning to feel like a data scientist. 
This level of confidence quickly dropped off when I started modeling and managing my variables. 50 hours of coding later, I can now appreciate the challenges associated with making any sort of predictive model. After several different iterations of my model, I arrived on a final predictive model with 7 independent variables: 2 continuous and the other 5 categorical. Despite my best attempts using recursive feature elimination and train-test-split, I was only able to achieve an R-square of 0.588 for this model. Below I outline the 3 biggest challenges I ran into during the completion of the project. 

**Challenge 1: Making Location Data Useful**
When I began thinking about how to approach this project, I knew I would have to find a way to include location or a map. As anyone who has bought or rented a house knows, real estate prices are heavily driven by location/neighborhood. However, I knew that I could not include latitude or longitude in my linear regression model because those points weren’t really continuous or categorical variables in the traditional sense. In order to give the non-technical stakeholder a clear picture of where high priced and low priced homes are in the Kings County area, I plotted all of the data points on a folium map. Then, I split that data by quartile of price, and color coded my map accordingly. This had the desired effect: creating a “heat map” of sorts that shows where the most and least expensive neighborhoods are. Furthermore, folium’s built-in marker function allowed me to make this map interactive. As the user looks at different areas of the map to see what homes sold for in that area, the user can click on any of the points and find out the actual price, the square footage, and the number of bedrooms. I imagine that this sort of interactive map is exactly the kind of thing that someone with a non-technical background would find helpful when looking to buy or sell a house in the area. 

**Challenge 2: Wrangling and Manipulating Data**
This dataset proved more difficult than I had initially perceived because there are many variables which appear as continuous but are actually categorical. Before doing any real data exploration, I believed that grade would be a great continuous variable predictor for price. However, as I learned more about the different grade levels and their qualitative features, I realized that I would have to treat it as a categorical variable instead of a continuous one. Furthermore, I found most of my other non-square footage variable were also categorical. In order to create the best regression model possible, I binned each of my categorical variables into bins that made sense for analysis. 
The continuous variables also gave me more trouble than I anticipated they would. As I began visualizing my potential predictors, I found that all of the square footage variables were heavily skewed to the right and therefore required transformation. I log transformed and then standardized all of my variable for maximum comparability. I applied log transformations to the data, but as I began my regression I was getting less than ideal R-squared values and couldn’t figure out why. I investigated the distribution of my dependent variable price, and found that price too was skewed to the right and required transformation. Initially, I was hesitant about transforming price at all because it would make the interpretation of the model coefficient outputs more difficult. Before being able to predict any sort of price, transformations would be required on both inputs and output. For example, a simple regression equation would have the following coefficient interpretation.

Price = intercept +29.5(sqft_living)

The interpretation for this is rather simple: for every additional square foot of the house, we expect price to increase by $29.5. 

However my regression formulas were looking more like this:

Logprice = intercept +0.347(log(standardized(sqft_living))

The interpretation for this formula is much more complicated, especially for someone without a technical background: for every one unit increase in the log of standardized sqft_living, we predict log(price) to increase by 0.347. 
These coefficients can obviously still be used to create an effective model, but interpreting their coefficients takes more effort and a bit of calculation. 

**Challenge 3: Overfitting the Data**
As I was experimenting with recursive feature elimination and test-train split, I found that my model seemed to achieve a better R-squared if I used more and more predictors. Excluding all of the predictors which I eliminated during exploratory data analysis due to multicollinearity or lack of meaningful data, I ended up including ALL of my predictors in my final model. This included two continuous variables and five categorical variables. I thought that this was odd, because some of my categorical variables didn’t have great R-squared values on their own, but they seemed to be improving the models R-squared. However, recursive feature elimination, test-train-split, and 10-fold cross validation didn’t indicate that there was any problem with my model. The labs/readmes mention that AIC can be used to determine if a model is overfitted, but I couldn’t figure out how to use that as a gauge. I think that it is entirely possible my model is overfitted, and I look forward to discovering solutions to help resolve this!

