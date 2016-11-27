# Chapter 4: Classification

#### Why Not Linear Regression?

In general there is no natural way to convert a qualitative response variable with more than two levels into a quantitative response that is ready for linear regression. We cannot quantize the relationship between multiple categories since we know nothing about them.

If this is binary classification linear regression does work. But it is not the best of methods.

##### The Logistic Model

We use a logistic function which can only go from 0 to 1 to model probabilities.
To fit the model, we use a method called *maximum likelihood*.
 We see that the logistic regression model has a logit(log-odds) that is linear in X. In a logistic regression model, increasing X by one unit changes the log odds by β1
 
#####  Estimating the Regression Coefficients

Although we could use (non-linear) least squares to fit the model, the more general method of maximum likelihood is preferred, since it has better statistical properties. 

The basic intuition behind using maximum likelihood to fit a logistic regression model is as follows: we seek estimates for β0 and β1 such that the predicted probability p(xi) of default(credit default) for each individual, corresponds as closely as possible to the individual’s observed default status. In other words, we try to find βˆ0 and βˆ1 such that plugging these estimates into the model for p(X), yields a number close to one for all individuals who defaulted, and a number close to zero for all individuals who did not. This intuition can be formalized using a mathematical equation called a *likelihood function*.

The estimates β ˆ0 and β ˆ1 are chosen to maximize this likelihood function. 

Maximum likelihood is a very general approach that is used to fit many of the non-linear models that we examine throughout this book. In the linear regression setting, the least squares approach is in fact a special case of maximum likelihood. 

##### Making Predictions

Pretty straight forward

##### Multiple Logistic Regression

This example used in the book illustrates the dangers and subtleties associated with performing regressions involving only a single predictor when other predictors may also be relevant. As in the linear regression setting, the results obtained using one predictor may be quite different from those obtained using multiple predictors, especially when there is correlation among the predictors. In general, the phenomenon is known as confounding.

#### Linear Discriminant Analysis

Logistic regression involves directly modeling Pr(Y = k|X = x) using the logistic function, for the case of two response classes. In statistical jargon, we model the conditional distribution of the response Y , given the predictors X. We now consider an alternative and less direct approach to estimating these probabilities. In this alternative approach, we model the distribution of the predictors X separately in each of the response classes (i.e. given Y ), and then use Bayes’ theorem to flip these around into estimates for Pr(Y = k|X = x). When these distributions are assumed to be normal, it turns out that the model is very similar in form to logistic regression.

**Why do we need another method, when we have logistic regression?**

1. When the classes are well-separated, the parameter estimates for the logistic regression model are surprisingly unstable. Linear discriminant analysis does not suffer from this problem.
2. If n is small and the distribution of the predictors X is approximately normal in each of the classes, the linear discriminant model is again more stable than the logistic regression model.
3. linear discriminant analysis is popular when we have more than two response classes.

##### Using Bayes’ Theorem for Classification

Suppose that we wish to classify an observation into one of K classes, where K ≥ 2. In other words, the qualitative response variable Y can take on K possible distinct and unordered values. Let π(k) represent the overall or prior probability that a randomly chosen observation comes from the kth class; this is the probability that a given observation is associated with the kth category of the response variable Y . Let fk(X) ≡ Pr(X = x|Y = k) denote the density function of X for an observation that comes from the kth class. In other words, fk(x) is relatively large if there is a high probability that function an observation in the kth class has X ≈ x, and fk(x) is small if it is very unlikely that an observation in the kth class has X ≈ x. 

######  Linear Discriminant Analysis for p = 1

The linear discriminant analysis (LDA) method approximates the Bayes classifier by plugging estimates for πk, μk, and σ2 calcualted from samples. 

The word linear in the classifier’s name stems from the fact that the discriminant functions δˆk(x) are linear functions of x.

To reiterate, the LDA classifier results from assuming that the observations within each class come from a normal distribution with a class-specific mean vector and a common variance σ2, and plugging estimates for these parameters into the Bayes classifier.

###### Linear Discriminant Analysis for p >1


