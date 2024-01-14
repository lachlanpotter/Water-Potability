# Water Potability Prediction
In this repository we gather data and train an AI to predict the potability of water based on measured characteristics e.g. pH, Turbidity, Sulfides...


# Table of contents
 [Dataset Formation](#data-formation)
 [Data Analysis](#data-analysis)
 [Model Selection](#selection)
 [Results Analysis](#results)


# Dataset Formation <a name="data-formation"></a>
We imported our dataset as a CSV file obtained from [kaggle](https://www.kaggle.com/datasets/uom190346a/water-quality-and-potability) using pandas, and did some preliminary cleaning using pandasql commands. Cleaned data consisted of roughly 2000 water samples, with a roughly 40/60 split between potable water and non-potable samples.

# Data Analysis <a name="data-analysis"></a>
Histogram plots of our data using the matplotlib library revealed that most of our data was roughly normally distributed, so there was no need to logarithmically scale any of our variables before normalisation.

The seaborn heatmap of our data showed that our variables were uncorrelated with each other, and also uncorrelated with potability of the water, meaning that it was not necessary to remove any redundant variables.

# Model Selection <a name="selection"></a>
After a general parameter tuning of each of the five candidate models (logistic regression, k-nearest neighbours, naive Bayes, random forest classifier, gradient boosted trees) the random forest classifier had the highest accuracy, and was chosen for further tuning.

# Results Analysis <a name="results"></a>
The final model makes the correct prediction 64% of the time, which may not seem very good, but looking a little closer at the confusion matrix we can see what is going on.

The model is very conservative in predicting that a given sample is potable, predicting potability only 10% of the time. However, the model only suggests drinking a sample that is unsafe to drink about 3% of the time. This is probably the direction of bias I would want for a model like this, so I am not too unhappy with the result.

It would be nice to raise the overall accuracy of the model somehow, and improve its accuracy at identifying potable water. Overall this model is probably best used for ruling samples of water as *unsafe* to drink, rather than as a greenlight to go ahead and drink the sample.