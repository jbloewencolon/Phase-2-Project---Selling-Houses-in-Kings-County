# The Garage Problem: Real Estate Recommendations for Kings County California

![garage](http://nccarpentry.com/uploads/3/4/1/7/34171415/1441711_orig.jpg)
    
By Jordan Loewen-Colón October 14th 2022

# The Business Problem

King's County Realtors are interested in whether or not they should renovate homes before trying to sell. Specifically, they'd like to know how much adding a garage might affect price, and if so, what size of garage.

# Recommendations:

Based on our models and analysis, we recommend that if rennovations are going to occur, its best to target square footage of living space, but if renovations are going to includ the garage, it is probably worth focusing on homes that have no garage and adding a 1-car sized garage, rather than increasing the size of an existing garage.

# Step 1: Data Understanding

We will analyze the 2022 data from King's Country to try and offer accurate recommendations.

We begin by importing the proper tools and then the data itself.

# Step 2: Data Preperation

* In preparing the data, we will primarily focus on elements we think will affect our numbers involving renovations broadly, and garage additions more specifically. Since we are dealing with both continuous numbers and integers, we may end up needing some log transformations. We will test our model by looking at the correlation between price per sqft of house. According to according to the website www.fixr.com the cost of building a home in California is roughly "400 and 600 per square foot." So that will be a good target for checking the accuracy of our data prep.

# Data Modeling

Now with our data prepared and in hand, it's time to create some models. First, we will check to see the accuracy of our data preperation by checking price per sqft.

# Data Understanding

Results of model:
This model explains about 53.3% of the variance in our data
This models F-statistic is statatistically significant compared to our alpha of 0.05
Most of the coefficients are statistically significant when compared to our alpha of .05

Interpretations:
For a house with no garage, of average grade and condition, and with no renovations we would expect the house to about 70k less than a home that is renovated.
We expect that same house to sell for about 4k more with a 1-car garage
For each additional 1 square foot in living space size and all other features remaining the same, we would expect the house to gain about $263

# Conclusion

According to our models, renovating a home, specifically targeting square footage of living space, will have a significant increase on the value of the home. While it looks like adding a garage can increase the value of a home in some scenarios, it is dependent on the size of garage and other factors. We would be hard pressed to recommend adding a 1-car garage to a home that does not have one, given that the price difference is only about 4k increase.

To that end, based on our models and analysis, we recommend that if rennovations are going to occur, its best to target square footage of living space, but if renovations are going to includ the garage, it is probably worth focusing on homes that have no garage and adding a 1-car sized garage, rather than increasing the size of an existing garage.

# Next Steps

With more time, we could include other factors, like zip cope, that might increase the accuracy of our model and thus update our recommendations.

# Questions?
For a full analysis please check the Jupyter Notebook or slide presentation.
Further questions? Contact Jordan Loewen-Colón @ jbloewen@syr.edu

## Repository Structure


```
├── data : data used for modeling
├── images : images used in PPT and README
├── Microsoft Movie Studio.ipynb : notebook used to pull from API
├── README.md : project information and repository structure
├── presentation.pdf : the powerpoint presentation used to present data analysis
