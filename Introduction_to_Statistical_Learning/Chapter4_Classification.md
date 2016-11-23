# Chapter 4: Classification

#### Why Not Linear Regression?

In general there is no natural way to convert a qualitative response variable with more than two levels into a quantitative response that is ready for linear regression. We cannot quantize the relationship between multiple categories since we know nothing about them.

If this is binary classification linear regression does work. But it is not the best of methods.

##### The Logistic Model

We use a logistic function which can only go from 0 to 1 to model probabilities.
To fit the model, we use a method called *maximum likelihood*.
 We see that the logistic regression model has a logit(log-odds) that is linear in X. In a logistic regression model, increasing X by one unit changes the log odds by β1
 
#####  Estimating the Regression Coefficients

