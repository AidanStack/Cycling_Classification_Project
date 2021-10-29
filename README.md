# Repo Structure

.gitignore - Our dataset has nearly 2 million rows, making it far too large for github. Data source is linked at the bottom of this README

Main Analysis Notebook - Our entire data science process for this project. 

README - YOU ARE HERE


# Business Problem and Overview

Our proposed client is the City of New York itself. The city government has come under fire from constituents and cyclist advocacy groups for the dangerous conditions cyclists endure. The city's transportation leadership want to know what conditions lead to deadly traffic collisions for New York's cyclists. The classification model in this instance is not the end product, as once the city has a record of the accident, they already know if a cyclist has died or not. The final product of this analysis will be the emergent patterns revealed by what parameters make for a classification model capable of predicting fatal cycling accidents. Our data comes from the NYC Open Data project.

# 1. Data Understanding

In this phase of exploratory data analysis, we look over our dataset to find out what cleaning and preprocessing steps it requires before we will be able to apply Scikit Learn models. This is also the section where we discover just how severe the imbalance of our dataset is, with only .5% of our data in our minority class (lethal collisions).

# 2. Data Cleaning

This step is critical for our analysis, as the data straight out of the csv from NYC Open Data is messy, filled with NaN values, and lacks certain columns we will want to use in our modeling process. The data cleaning is simply a matter of methodically going through each of the original columns, and manipulating the data into the formats we need. 

# 3. Preprocessing

To avoid any possible data leakage that could hurt the validity of our final model, we performed two train test splits. The first separated our data into training data and holdout data, then the second split separated our training data into training and test data, so that when iterating on our models, we could test each iteration as we went on the test set. We then set up a Pipeline containing all of our preprocessing steps, for consistency and ease of use later on at final model evaluation time. 

# 4. Model Type Exploration

We knew that our final model was never going to perform well, due simply to the extreme imbalance in our dataset. However we still wanted the best possible model, so we took the kitchen sink approach and ran all kinds of classification algorithms through grid searches, eventually trying thousands of models. In the end however logistic regression looked the most promising. 

# 5. Modeling Iterations

Once we knew that Logistic Regression was our classifier of choice, we ran an even more extensive grid search until we had the best model we could make. 

# 6. Model Evaluation and Feature Analysis 

With our final model in hand, we could assemble it into a pipeline with our preprocessor, and fit to our holdout data. Our model performed as well as we could have hoped, with an accuracy of 72% and a recall of 68.75%. This is exactly what we expected to get, as in this business case, false positives are more desirable than missing false negatives. The cases where we got false positives point to collisions with input conditions that the model can tell are more likely to be lethal, and possibly weren't lethal due to chance. False positives are also more tolerable because the constituents currently criticizing city leadership will not be angered by making some streets safer than needed. 

# 7. Key Takeaways and Next Steps

1. Large Trucks and Buses. One of the most effective changes the city could enact is to figure out how to reduce the number of cyclists killed by large vehicles. Whether this means changes to bike lane infrastructure, restricting which streets large vehicles can drive on, cyclist safety training programs, or special training for city bus drivers and people who have commercial drivers licenses in NYC. 
2. Zipcode. As the second strongest indicator of lethality, zipcode is an aspect to crashes that cannot be ignored by the city. Luckily this indicator is highly informative for the city in terms of where geographically to focus their efforts. 
3. Brooklyn. With a huge number of cyclists, Brooklyn is definitely another piece of the geographical puzzle when it comes to the city reducing cycling fatalities. 
4. Time of Day. The city could do a lot by cracking down on drunk and reckless driving in the late night and early morning, as well as run campaigns urging cyclists to wear more visible clothing and use lights after sundown. More traffic control officers during rush hour could also make a large difference. 

Possible Next Steps
1. Fill in NaN values in Borough and Zipcode using latitude and longitude data. 
2. Build an intersection feature using Street and Cross Street that finds the cities most dangerous intersections. 
3. Look at bicycles vs E-Bikes in terms of collision lethality. 


Presentation Link: https://www.canva.com/design/DAEuDWwpohA/1pH6i6Tejg5N8YkQkCM45Q/view?utm_content=DAEuDWwpohA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

NYC Open Data Motor Vehicle Collisions: https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95/data
