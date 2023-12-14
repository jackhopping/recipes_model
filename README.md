# recipes_model
**This repository contains an overview of a data modeling project I completed for DSC 80 at UC San Diego.** , 

## Framing the Problem

My model will be a classification model which predicts recipe ratings based on the features "minutes" and "n_steps".

### Feature Types

- Ratings: Categorical Ordinal
- Minutes: Quantitative Discrete
- N_steps: Quantitaticve Discrete

## Baseline Model

My baseline model consists of two predictor features, ```n_steps``` and ```minutes```. I did not need to perform any categorical transformations, since both features are quantitative. The performance metrics of the model are shown below:

**Baseline Metrics:**
- Train Precision: ```0.7364680023644379```
- Test Precision: ```0.6478012759804213```
- Train F1: ```0.6840155662030893```
- Test F1: ```0.6774356466520753```

## Final Model

In the final model I had a total of four features: ```n_steps``` and ```minutes``` from my baseline model, as well as ```n_ingredients``` and ```avg recipe rating```. The reason I decided to add each of these additional features is that I believe simpler recipes, with less ingredients, would have higher ratings overall because they are cheaper and easier for the average person to cook than a recipe with many ingredients, and the average recipe rating can indicate what an individual rating is likely to be.

The feature engineering that I performer was a log transformation on the "N-steps" and "minutes" columns. Both were heavily skewed right, as shown in the histograms below.

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
- Train F1: ```0.8524856452573817```
- Test F1: ```0.7783913021187199```

Overall, my final model performed better than my baseline model.

## Fairness Analysis