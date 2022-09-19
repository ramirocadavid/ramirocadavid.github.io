---
layout: page
title: "The Askeladden Algorithm"
permalink: /projects/askeladden-algorithm/
---
*Ramiro Cadavid, Anna Jacobson, Laura Pintos*

*Published in [Medium](https://medium.com/towards-data-science/the-askeladden-algorithm-10859c349fc9)*

A machine learning project to develop an algorithmic classification system to help Twitter to identify Internet Research Agency “fake news” Russian troll tweets.

## Motivation

In the context of the US Department of Justice investigation into Russian State sponsored and coordinated disinformation campaign, Twitter has identified and suspended thousands of malicious accounts, deleting millions of the trolls’ tweets from public view on the platform. While other news outlets have published samples, it has been difficult to understand the full scale and scope of the Russian's IRA (Internet Research Agency) efforts, as well as the details of its strategy and tactics.

The fact that there was a clear intent to undermine the US civil and political institutions, the potential impact that this could have in the US and the world and the effectiveness with which these trolls were able to infiltrate American political conversation makes shedding light on this phenomenon worth of our attention and, we believe, of the broader research community.

The purpose of this project is to understand IRA trolls' behavior by describing their most salient features and develop a machine learning algorithm to predict "fake news" troll tweets. Our algorithm is named after Askeladden, a boy in Norwegian folklore who outwits trolls.

## Data sources

In late 2018 Twitter made publicly available archives of Tweets and media that it believed resulted from potentially state-backed information operations. We complemented this dataset by scraping tweets from real US based news outlets, using `TweePy` Python library, to build a balanced dataset that contained both fake and "real" news. Given the limitations to retrieve tweets from Twitter, we had to select a random sample from these two source to obtain approximately 153,000 tweets for each class.

<img src="/assets/images/askeladden-data-sampling.jpg" width="900" class="center">

## Troll prediction model

### Model training

To define the final model that was trained in the full dataset, we tested different models with different parameter values, using the accuracy of each model as their main performance metric. The summary of the models tested with their obtained accuracy in the test set are shown below.

<img src="/assets/images/askeladden-models.jpg" width="900" class="center">

The two models with the highest performance were logistic regression with bigram feature extraction and an ensemble of multiple representations. Even though the latter had a slightly higher performance, the former is much more parsimonious, has faster training and inference times and is more interpretable. For this reason, we selected the logistic regression and further tuned its hyperparameters, obtaining a higher performance than its previous version.

<img src="/assets/images/askeladden-final-model.jpg" width="900" class="center">

An analysis of the model's calibration further shows that it is fairly well callibrated.

<img src="/assets/images/askeladden-model-calibration.jpg" width="900" class="center">

### Model implementation

To be useful, the resulting model needs to balance the trade-off between correctly identifying trolls (i.e. true positives) and incorrectly identifying real accounts as trolls (i.e. false positives). Ultimately, there are judgement values and practical business and legal criteria that will need to be taken into account to set the optimal balance between these, which falls outside of the scope of this project. However, we can provide elements that help illustrate how this trade-off behaves for different thresholds and the implications of selecting different thresholds.

In order to ensure that real news isn’t mistakenly classified as trollish, we must establish a required level of accuracy to “convict” a troll. Using calibration, we can then set a confidence threshold for conviction using the posterior probability.

<img src="/assets/images/askeladden-confidence-thresholds.jpg" width="900" class="center">

The following chart exemplifies how the final choice of classification threshold impacts our ability to correctly detect trolls.

<img src="/assets/images/askeladden-implementation.jpg" width="900" class="center">

## Troll tactics

Furthermore, were able to identify key features of the troll's tactics to be able to embed themselves in the conversation and change the content and tone of the conversation.

Camouflage: large proportion of "neutral" posts

<img src="/assets/images/askeladden-camouflage.jpg" width="700" class="center">

Confusion: tweets often sound like real news tweets

<img src="/assets/images/askeladden-confusion.jpg" width="700" class="center">

Variation: The top fifty most predictive features of a troll tweet are seemingly varied. However, upon closer examination, patterns emerge in the trolls' tweets.

<img src="/assets/images/askeladden-variation.jpg" width="700" class="center">

## Skills and Tools

Programming | Python (TweePy, Pandas, Numpy, Matplotlib, ScikitLearn, PandasML, WordCloud, Gensim), Jupyter Notebook
Exploratory data analysis | Text analysis, data visualization
Statistics | sampling methods, descriptive statistics
Machine learning | Grid search, hyperparameter tuning, TF-IDF, natural language processing (NLP), logistic regression, naive Bayes, ensemble methods, Doc2Vec, distributed bag of words, distributed memory concatenation, distributed memory mean
