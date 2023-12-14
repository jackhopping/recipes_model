# recipes_model
**This repository contains an overview of a data modeling project I completed for DSC 80 at UC San Diego.** , 

## Framing the Problem

My model will be a classification model which predicts recipe ratings based on the features "minutes" and "n_steps".

### Feature Types

- Ratings: Categorical Ordinal
- Minutes: Quantitative Discrete
- N_steps: Quantitaticve Discrete

## Baseline Model

<iframe src="assets/n-steps-hist.html" width=600 height=600 frameBorder=0></iframe>

<iframe src="assets/minutes-hist.html" width=600 height=600 frameBorder=0></iframe>

<iframe src="assets/ratings-hist.html" width=600 height=600 frameBorder=0></iframe>

My baseline model consists of two predictior features, ```n_steps``` and ```minutes```. I did not need to perform any categorical transformations, since both features are quantitative. The performance metrics of the model are shown below:

**Baseline Metrics:**
- Train Precision: ```0.7364680023644379```
- Test Precision: ```0.6478012759804213```
- Train F1: ```0.6840155662030893```
- Test F1: ```0.6774356466520753```

## Final Model

In the final model I had a total of four features: ```n_steps``` and ```minutes``` from my baseline model, as well as ```n_ingredients``` and ```avg recipe rating```. The reason I decided to add each of these additional features is that I believe simpler recipes, with less ingredients, would have higher ratings overall because they are cheaper and easier for the average person to cook than a recipe with many ingredients, and the average recipe rating can indicate what an individual rating is likely to be.

I chose to use DecisionTreeClassifier for my model. I was debating between DecisionTreeClassifier and RandomForestClassifier, but chose the former because I do not think my model is overly complex, and wanted to choose a classifier that would run quickly and accurately.

After running a GridSearchCV, I found that the optimal hyperparameters were as follows:


**Final Model Metrics:**
- Train Precision: ```0.8153649411449584```
- Test Precision: ```0.8160505433151705```
- Train F1: ```0.8030270019924108```
- Test F1: ```0.8024801563510491```

## Fairness Analysis