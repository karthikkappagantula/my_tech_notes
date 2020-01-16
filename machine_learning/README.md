# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Important URLs](#important-urls)
  - [Introduction](#introduction)
  - [Supervised Learning](#supervised-learning)
    - [Classification](#classification)
    - [Regression or Prediction](#regression-or-prediction)
  - [Unsupervised Learning](#unsupervised-learning)
    - [Clustering](#clustering)
    - [Association Rule Mining](#association-rule-mining)
  - [Reinforcement Learning](#reinforcement-learning)
  - [Statistical Decision Theory](#statistical-decision-theory)
    - [Regression](#regression)

## Important URLs


## Introduction

```"A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P if its performance at tasks in T, as measured by P, improves with experience E."```
*- Tom Mitchell*

**ML paradigms** - 
* Supervised Learning - Learn an input and output map
  * Classification : categorical output
  * Regression : continuous output
* Unsupervised Learning - Discover patters in the data
  * Clustering : cohesive grouping
  * Association : frequent cooccurence
* Reinforcement Learning - Learning to control behaviour of systems

**Key Challenges behind building ML systems**
* How do i choose a model?
* How good is a model?
* Do I have enough data?
* Is the data of sufficient quality?
  * Errors/Noise in data
  * Missing values
* How confident can I be of the results?
* Am I describing the data correctly?
  * Are age and income enough? Should I look at Gender also?
  * How should I represent age? As a number, or as young, middle age, old?

## Supervised Learning

### Classification 

* Classifies the output in to categories based on the data which is discrete in nature.
* Should be able to make some assumption to create the model based on the input data distribution and labels.
  * Language bias
  * Search biad

* **Training Set** is a labelled output that is fed in to a Training model.
* **Test Set** is a unlabelled output that is used for validation of the model.
* As a general practise the input data is normalized before feeding to Training model.


* Applications of Classification
  * Credit card fraud detection
    * Valid transaction or not
  * Sentiment Analysis
    * Opinion mining; buzz analysis; etc.
  * Churn prediction
    * Potential churner or not
  * Medical diagnoses
    * Risk analysis

### Regression or Prediction

* Make predictions based on continuous input data.
* **Linear Regression** 
  * Minimise sum of squared error
  * With sufficient data simple enough
  * With many dimensions, challenge is to avoid over fitting
    * Regularization
  * Higher order functions?
    * Basis transformations
    * Ex: (x1, x2) -> (x1^2, x2^2, x1x2, x1, x2)

* Applications of Regression
  * Time series predictions
    * Rainfall in a certain region
    * Spend on voice calls
  * Classification
  * Data reduction
  * Trend analysis
    * Linear or exponential
  * Risk factor analysis
    * Factors contributing most to output

## Unsupervised Learning

### Clustering

* Group the unlabelled input data in to clusters based on some bias.

* Applications of Clustering
  * Customer Data
    * Discover classes of customers
  * Image pixels
    * Discover regions
  * Words
    * Synonyms
  * Documents
    * Topics

### Association Rule Mining
* Mining frequent patters and rules
* Association rules: conditional dependencies
* Two Stages
  * Find frequent patterns
  * Derive association (A => B) from frequent patters
* Find patterns in 
  * Sequences (time series data, fault analysis)
  * Transactions (market basket data)
  * Graphs (social network analysis)

* Mining Transactions
  * Transaction is a collection of items bought together
    * A (sub)set of items is called an itemset
  * Find frequent itemsets
  * Itemset A => Itemset B, if both A and A U B are frequent itemsets.

* Applications of Association
  * Predicting co-occurence
  * Market Basket analysis
  * Time series analysis
    * Trigger Events
  
## Reinforcement Learning
**Learning to Control**
* Popular models of Machine Learning
  * Supervised: Classificiation, Regression, etc.
  * Unsupervised: Clustering, Frequent patterns, etc.

* How did you learn to cycle?
  * Neither of the above models help
  * Trial and error
  * Falling down hurts

* Applications of Reinforcement Learning
  * Game playing
    * Backgammon 
    * Video games from scratch
  * Autonomous agents
    * Robot navigation
  * Adaptive control
    * Helicopter pilot
  * Combinatorial optimization
    * VLSI placement
  * Intelligent Tutoring Systems / Recommendation models

## Statistical Decision Theory

### Regression
