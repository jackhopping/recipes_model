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

** Baseline Metrics: **
- Train Precision: ```0.7364680023644379```
- Test Precision: ```0.6478012759804213```
- Train F1: ```0.6840155662030893```
- Test F1: ```0.6774356466520753```

## Final Model

** Final Model Metrics: **
- Train Precision: ```0.8153649411449584```
- Test Precision: ```0.8160505433151705```
- Train F1: ```0.8030270019924108```
- Test F1: ```0.8024801563510491```

## Fairness Analysis