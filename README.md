# Solving the Garage Problem: 
## Real Estate Recommendations for King County, Washington
![garage](http://nccarpentry.com/uploads/3/4/1/7/34171415/1441711_orig.jpg)
    
By Jordan Loewen-Colón October 14th 2022

# The Business Problem

King County Realtors are interested in whether or not they should renovate homes before trying to sell. Specifically, they'd like to know how much adding a garage might affect price, and if so, what size of garage. However, they need the inferences within a couple of days, and data is limited! The location of each home is missing, and without location data (location is key for real estate!), how accurate can any model really be?

# Recommendations:

Based on our models and analysis, we recommend that if renovations are going to occur, it's best to target the square footage of living space, but if renovations are going to include the garage, it is probably worth focusing on homes that have no garage and adding a 1-car sized garage, rather than increasing the size of an existing garage.

# Step 1: Data Understanding

To make our recommendations, we analyzed the 2022 data from King's County.

The dataset has 30155 entries and 25 columns with a mix of string values, floats, and integers. Bathrooms as float makes sense, but "floors" as float seems odd. It was also unclear what elements were contained in some object categories like "grade" or "nuisance." There were also some missing entries for "sewer_system" and "heat_source." One odd thing we noticed initially is that there were houses without bedrooms or bathrooms. There were also outliers on the larger end as well, with houses containing 13 bedrooms and 10.5 bathrooms. There was even a house listed with only 3 sqft of living space. It also became clear that we were going to need to separate out the houses that already have garages from those that do not.

![heatmap](https://github.com/jbloewencolon/Phase-2-Project---The-Garage-Problem/blob/main/Images/heatmap.JPG)

Given that are focus is on garages, it's important to note that there are both houses with no garages or which have never been renovated. In narrowing down, we noticed that columns like "waterfront" and "greenbelt" had few entries, so they probably would not add much to our analysis. Additionally, given time constraints, we couldn't spend time on categories like "date, view, sqft_above, sqft_basement." And for the sake of this exercise (and its time constraints), we are pretending "address, lat, and long" were not included in the dataset. So we ended up focusing primarily on "yr_renovated," "condition," "grade," and, especially, "sqft_living" as categories in order to build the most accurate model.

# Step 2: Data Preperation

In preparing the data, we focused on elements we thought would affect our numbers involving renovations broadly and garage additions more specifically. Since we were dealing with both continuous numbers and integers, we experimented with log transformations but didn't find their adjustments useful and getting a more accurate model. To check the accuracy of our model, we focused primarily on the correlation between price per sqft of house. According to the website [www.redfin.com](https://www.redfin.com/county/118/WA/King-County/housing-market) the average price per sqft is $453. So we thought that would be a good target for checking the accuracy of our data prep.

With price as our major target, we set it as our Y and looked for correlations with the other columns as our x's.

![plots](https://github.com/jbloewencolon/Phase-2-Project---The-Garage-Problem/blob/main/Images/multiple%20regression.JPG)

Since scatterplots are more useful at visualizing the relationship with continuous data, we adjusted columns like "grade" and "condition" by turning them from strings to integers which allowed our model to see the relationship between the numbers more clearly and hopefully give us more accuracy. We then dealt with outliers, which filtered out 2513 rows from our set of 30155.

We then created new columns checking for which houses had garages and which ones didn't, in addition to a new column for garages based on size (either 1-car, 2-car, or 3-car).

# Data Modeling

Now, with our data prepared and in hand, we created some models. First, we checked the accuracy of our data preparation by checking the price per sqft.

![Model1](https://github.com/jbloewencolon/Phase-2-Project---The-Garage-Problem/blob/main/Images/Model%201.JPG)

So the coefficient is within the right range, but the R-squared is very low. However, transforming the number logarithmically actually lowers our R-value. So we kept it as it was and then added our other variables until we achieved the highest R-value given our selected data:

![Model2](https://github.com/jbloewencolon/Phase-2-Project---The-Garage-Problem/blob/main/Images/model%202.JPG)

# Data Understanding

Results of model:
This model explains about 53.3% of the variance in our data
This model's F-statistic is statistically significant compared to our alpha of 0.05
Most of the coefficients are statistically significant when compared to our alpha of .05

Interpretations:
For a house with no garage, of average grade and condition, and with no renovations, we would expect the house to be about 70k less than a renovated home.
We expect that same house to sell for about 4k more with a 1-car garage
For each additional 1 square foot in living space size and all other features remaining the same, we would expect the house to gain about $263

# Conclusion

According to our models, renovating a home, specifically targeting square footage of living space, will significantly increase the home's value. While adding a garage can increase the value of a home in some scenarios, it depends on the garage's size and other factors. We would be hard-pressed to recommend adding a 1-car garage to a home that does not have one, given that the price difference is only about a 4k increase.

To that end, based on our models and analysis, we recommend that if renovations are going to occur, it is best to target the square footage of living space, but if renovations are going to include the garage, it is probably worth focusing on homes that have no garage and adding a 1-car sized garage, rather than increasing the size of an existing garage.

# Next Steps

With more time, we could include other factors, like zip cope, that might increase the accuracy of our model and thus update our recommendations.

# Questions?
For a full analysis, please check the Jupyter Notebook or slide presentation.
Further questions? Contact Jordan Loewen-Colón @ jbloewen@syr.edu

## Repository Structure


## Repository Structure

├── [data](https://github.com/jbloewencolon/Solving-the-Garage-Problem-for-Kings-County/tree/main/Data) : data used for modeling
├── [images](https://github.com/jbloewencolon/Solving-the-Garage-Problem-for-Kings-County/tree/main/Images) : images used in PPT and README
├── [garage-problem.ipynb](https://github.com/jbloewencolon/Solving-the-Garage-Problem-for-Kings-County/blob/main/The%20Garage%20Problem.ipynb) : notebook used to pull from API
├── [README.md](https://github.com/jbloewencolon/Solving-the-Garage-Problem-for-Kings-County/blob/main/README.md) : project information and repository structure
├── [presentation.pdf](https://github.com/jbloewencolon/Solving-the-Garage-Problem-for-Kings-County/blob/main/presentation.pdf) : the PowerPoint presentation used to present data analysis

