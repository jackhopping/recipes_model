# recipes_model
**This repository contains an overview of a data modeling project I completed for DSC 80 at UC San Diego.** , 

## Framing the Problem

My model will be a multiclass classification model which predicts recipe ratings based on the features "minutes" and "n_steps".

### Feature Types

- Ratings: Categorical Ordinal
- Minutes: Quantitative Discrete
- N_steps: Quantitaticve Discrete

The response variable in my model is ```rating```. I chose this to be the response variable because it is arguably what people consider the most when deciding between options. In the specific example of a recipes dataset, a person is much more likely to choose a recipe that has 4 or 5 stars than one that has 1 star. Ratings influence our choices in so many ways, so I wanted to see what influences ```rating``` and how well I can predict ratings based on other features.

I am using precision as my evaluation metric because it measures how well a model avoids false positives - in this scenario, predicted high ratings when the actual rating is low.

## Baseline Model

My baseline model consists of two predictor features, ```n_steps``` and ```minutes```. I did not need to perform any categorical transformations, since both features are quantitative, and the only other transformation I performed was applying a StandardScaler since ```minutes``` and ```n_steps``` are not the same units. The performance metrics of the model are shown below:

**Baseline Metrics:**
- Train Precision: ```0.7364680023644379```
- Test Precision: ```0.6478012759804213```

## Final Model

In the final model I had a total of four features: ```n_steps``` and ```minutes``` from my baseline model, as well as ```n_ingredients``` and ```avg recipe rating```. The reason I decided to add each of these additional features is that I believe simpler recipes, with less ingredients, would have higher ratings overall because they are cheaper and easier for the average person to cook than a recipe with many ingredients, and the average recipe rating can indicate what an individual rating is likely to be.

The feature engineering that I performer was a log transformation on the "N-steps" and "minutes" columns. Both were heavily skewed right, as shown in the histograms below. A log transformation normalized the distributions, which will help my model's performance.

<iframe src="assets/n-steps-hist.html" width=600 height=600 frameBorder=0></iframe>

<iframe src="assets/minutes-hist.html" width=600 height=600 frameBorder=0></iframe>

I chose to use DecisionTreeClassifier for my model. I was debating between DecisionTreeClassifier and RandomForestClassifier, but chose the former because I do not think my model is overly complex, and wanted to choose a classifier that would run quickly and accurately.

After running a GridSearchCV, I found that the optimal hyperparameters were as follows:

- ```criterion```: ```entropy```
- ```max_depth```: ```7```
- ```min_samples_split```: ```200```

I trained a DecisionTreeClassifier on these hyperparameters, resulting in a test accuracy of 0.79.

The performance metrics of my final model are shown below:

**Final Model Metrics:**
- Train Precision: ```0.8505029379254765```
- Test Precision: ```0.7717957876681332```

Overall, my final model performed better than my baseline model. This performance is an improvement because the final model achieved a higher precision and a higher F1 score.

## Fairness Analysis