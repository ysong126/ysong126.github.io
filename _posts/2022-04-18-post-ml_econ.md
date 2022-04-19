---
title: The Gap between Machine Learning and Econometrics - Goals, Methods, and Settings 
categories:
- Econometrics
- Machine Learning
---


This article is inspired by Athey and Imben's paper. And for those of you who are curious about who they are, Guido Imbens won a Nobel prize in 2021 and he is married to Susan Athey. Their article has a comprehensive and informative discussion on the difference between econometrics and machine learning. 

## Goal
The first difference between machine learning and econometrics is the goal. Econometrics focuses on proposing an estimator that possesses nice properties. In technique terms, they are expected to be consistent, efficient, and normally distributed in large samples. If I were asked to explain this in common sense, I would say we want our coefficient to be predictable when we get more data. That is, when we collect more data on the same topic, our model does not change dramatically. Otherwise, it's useless. How much the model will change, then becomes the question. The setting here is somehow hypothetical and cyclical: We assume the model is specified correctly. If that is the case, we want the estimator, which is what we calculate using the data, to approach the true coefficient as our sample size grows. Beyond that, we want it to be close to the true value and stable. If we are looking at a linear model y = X*b, we want to find a b hat that is close to the true b, and even if we estimate a hundred times it's almost always close to it.

On the other hand, Machine Learning emphasizes the performance of the model in terms of prediction accuracy. In the example of y = X*b, we care about making accurate predictions of y hat, not b. An often-used metric is mean square error (y - predicted_y)^2. 

## Bias/Variance Tradeoff
when it comes to prediction, we want to make it fair. A standard approach Is a cross-validation. We split our sample into k partitions and iterate k times. in the kth iteration, we pretend that we don't have the access to the kth partition. Using the other (k-1) subsets to train our model, we want to test it on the "unseen" dataset. The reason that we have this out-of-sample evaluation is that we want to generalize our model. The intuition behind this is, that if we can always make our model predict accurately some data it has never seen before(but we have), it will be able to do that when we actually have new data coming in. On the contrary, proposing a model that always performs well on data it has access to but not on new data is less valuable. This type of model is called "overfitting". That means our model is emphasizing too much on predicting data that is already known(like economists). Compared with "overfitting", "underfitting" seems more undesirable. The canonical example is throwing a dart. A professional player could always hit the bull's eye or the area around it. For amateurs like myself, they should start with easier goals. For example, don't hurt anyone. There are two types of amateur players. One could hit the central area with a large spread. The other has a smaller spread but is always off in a certain direction. The spread in this example is called "variance" and the center of the player's darts to the bullseye is "bias".


  
