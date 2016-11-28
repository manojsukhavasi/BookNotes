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

We now extend the LDA classifier to the case of multiple predictors. To do this, we will assume that X = (X1, X2, . . . , Xp) is drawn from a multivariate Gaussian (or multivariate normal) distribution, with a class-specific multivariate mean vector and a common covariance matrix. 
 The multivariate Gaussian distribution assumes that each individual predictor follows a one-dimensional normal distribution, with some correlation between each pair of predictors.
 
 Once again, we need to estimate the unknown parameters μ1, . . . , μK, π1, . . . , πK, and Σ; We so that from sample estimates as in 1d case.
 
 To assign a new observation X = x, LDA plugs these estimates  and classifies to the class for which δ ˆk(x) is largest.

 Note that in δk(x) is a linear function of x; that is, the LDA decision rule depends on x only through a linear combination of its elements. Once again, this is the reason for the word linear in LDA.


##### Quadratic Discriminant Analysis

LDA assumes that the observations within each class are drawn from a multivariate Gaussian distribution with a class specific mean vector and a covariance matrix that is common to all K classes. 

QDA assumes that each class has its own covariance matrix.

the quantity x appears as a quadratic function unlike in LDA.

**why would one prefer LDA to QDA, or vice-versa?**

The answer lies in the bias-variance trade-off. 
When there are p predictors, then estimating a covariance matrix requires estimating p(p+1)/2 parameters. QDA estimates a separate covariance matrix for each class, for a total of Kp(p+1)/2 parameters. 

By instead assuming that the K classes share a common covariance matrix, the LDA model becomes linear in x, which means there are Kp linear coefficients to estimate

Consequently, LDA is a much less flexible classifier than QDA, and so has substantially lower variance. This can potentially lead to improved prediction performance. But there is a trade-off: if LDA’s assumption that the K classes share a common covariance matrix is badly off, then LDA can suffer from high bias. Roughly speaking, LDA tends to be a better bet than QDA if there are relatively few training observations and so reducing variance is crucial. In contrast, QDA is recommended if the training set is very large, so that the variance of the classifier is not a major concern, or if the assumption of a common covariance matrix for the K classes is clearly untenable.

#### A Comparison of Classification Methods

Though their motivations differ, the logistic regression and LDA methods are closely connected. 
Both of them produce log of odds in linear. Hence, both logistic regression and LDA produce linear decision boundaries. The only difference between the two approaches lies in the fact that β0 and β1 are estimated using maximum likelihood, whereas c0 and c1 are computed using the estimated mean and variance from a normal distribution. 

LDA assumes that the observations are drawn from a Gaussian distribution with a common covariance matrix in each class, and so can provide some improvements over logistic regression when this assumption approximately holds. Conversely, logistic regression can outperform LDA if these Gaussian assumptions are not met.

KNN is a completely non-parametric approach: no assumptions are made about the shape of the decision boundary. Therefore, we can expect this approach to dominate LDA and logistic regression when the decision boundary is highly non-linear. On the other hand, KNN does not tell us which predictors are important;

Finally, QDA serves as a compromise between the non-parametric KNN method and the linear LDA and logistic regression approaches. Since QDA assumes a quadratic decision boundary, it can accurately model a wider range of problems than can the linear methods. Though not as flexible as KNN, QDA can perform better in the presence of a limited number of training observations because it does make some assumptions about the form of the decision boundary.

When the true decision boundaries are linear, then the LDA and logistic regression approaches will tend to perform well. When the boundaries are moderately non-linear, QDA may give better results. Finally, for much more complicated decision boundaries, a non-parametric approach such as KNN can be superior. But the level of smoothness for a non-parametric approach must be chosen carefully.

