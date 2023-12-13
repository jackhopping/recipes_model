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

** Baseline Metrics: **
- Train Precision: ```0.7364680023644379```
- Test Precision: ```0.6478012759804213```
- Train F1: ```0.6840155662030893```
- Test F1: ```0.6774356466520753```

## Final Model

## Fairness Analysis