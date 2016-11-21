## Chapter 3: Linear Regression

#### Simple Linear Regression
It assumes that there is approximately a linear relationship between X and Y .

###### Estimating the Coefficients

###### Assessing the Accuracy of the Coefficient Estimates

- **Population regression line** : is the best linear approximation to the true relationship between X and Y
- **least squares line ** : can always be computed using the least squares method
-  In other words, in real applications, we have access to a set of observations from which we can compute the least squares line; however, the population regression line is unobserved.
-  Fundamentally, the concept of these two lines is a natural extension of the standard statistical approach of using information from a sample to estimate characteristics of a large population.
-  The concept of these two lines is a natural extension of the standard statistical approach of using information from a sample to estimate characteristics of a large population.
-  If we use the sample mean to estimate population mean, this estimate is unbiased, since on an average sample mean will be close to population mean. We are not systematically under estimating or over estimating
-  The property of unbiasedness holds for the least squares coefficient estimates given by as well
-  *Standard Error* : In general we can compute this, but we can estiamte this using *Residual Standard Error*, which is computed form RSS(Residual Sum of squares)
-  Standard errors can be used to compute confidence intervals. 

Standard errors can also be used to perform hypothesis tests on the coefficients. The most common hypothesis test involves testing the null hypothesis (There is no relationship between X and Y) or alternative hypothesis(There is some relationship between X and Y).

To test the null hypothesis, we need to determine whether β1^, our estimate for β1, is sufficiently far from zero that we can  be confident that β1 is non-zero. How far is far enough?

This of course depends on the accuracy of βˆ1—that is, it depends on SE(βˆ1). If SE(β ˆ1) is small, then even relatively small values of βˆ1 may provide strong evidence that β1 != 0, and hence that there is a relationship between X and Y . In contrast, if SE(βˆ1) is large, then βˆ1 must be large in absolute value in order for us to reject the null hypothesis. In practice, we compute a **t-statistic**, which measures the number of standard deviations that βˆ1 is away from 0. 
The t distribution has a bell shape and for values of n greater than approximately 30 it is quite similar to the normal distribution.

Consequently, it is a simple matter to compute the probability of observing any value equal to |t| or larger, assuming β1 = 0. We call this probability the p-value. Roughly speaking, we interpret the p-value as follows: a small p-value indicates that it is unlikely to observe such a substantial association between the predictor and the response due to chance, in the absence of any real association between the predictor and the response.

Hence, if we see a small p-value, then we can infer that there is an association between the predictor and the response. We reject the null hypothesis—that is, we declare a relationship to exist between X and Y —if the p-value is small enough. Typical p-value cutoffs for rejecting the null hypothesis are 5% or 1%

###### Assessing the Accuracy of the Model

The quality of a linear regression fit is typically assessed using two related quantities: the residual standard error (RSE) and the R^2 staistic.

**R2 Statistic** 

The RSE provides an absolute measure of lack of fit of the model to the data. But since it is measured in the units of Y , it is not always clear what constitutes a good RSE. The R2 statistic provides an alternative measure of fit. It takes the form of a proportion—the proportion of variance explained—and so it always takes on a value between 0 and 1, and is independent of the scale of Y

R^2 = 1- (RSS/TSS)

TSS measures the total variance in the response Y , and can be thought of as the amount of variability inherent in the response before the regression is performed. In contrast, RSS measures the amount of variability that is left unexplained after performing the regression. Hence, TSS − RSS measures the amount of variability in the response that is explained (or removed) by performing the regression, and R2 measures the proportion of variability in Y that can be explained using X. An R2 statistic that is close to 1 indicates that a large proportion of the variability in the response has been explained by the regression. A number near 0 indicates that the regression did not explain much of the variability in the response; this might occur because the linear model is wrong, or the inherent error σ^2 is high,or both.
The R2 statistic has an interpretational advantage over the RSE , since unlike the RSE, it always lies between 0 and 1. However, it can still be challenging to determine what is a good R2 value, and in general, this will depend on the application.

#### Multiple Linear Regression

The simple and multiple regression coefficients can be quite different. This stems form the fact that after taking into consideration on several features, some might have a correaltaion , so individually might be more significant than in multiple regression.

*Some of the important questions to address*

1. Is There a Relationship Between the Response and Predictors?
	we use a hypothesis test to answer this question. This hypothesis test is performed by computing the **F-statistic** 
    
    Hence, when there is no relationship (NULL hypothesis) between the response and predictors, one would expect the F-statistic to take on a value close to 1. On the other hand, if alterantive hypothesis is true, then we expect F to be greater than 1.
    
    However, what if the F-statistic had been closer to 1? How large does the F-statistic need to be before we can reject H0 and conclude that there is a relationship? It turns out that the answer depends on the values of n and p. When n is large, an F-statistic that is just a little larger than 1 might still provide evidence against H0. In contrast, a larger F-statistic is needed to reject H0 if n is small.
    
- [ ]     Page 76 and Page 77 needs to read again

2. Deciding on the important variables
	It is possible that all of the predictors are associated with the response, but it is more often the case that the response is only related to a subset of the predictors. The task of determining which predictors are associated with the response, in order to fit a single model involving only those predictors, is referred to as variable selection. 
    
    There are three classical approaches for this task:
    1. **Forward selection** : We begin with the null model—a model that contains an intercept but no predictors. We then fit p simple linear regressions and add to the null model the variable that results in the lowest RSS. We then add to that model the variable that results in the lowest RSS for the new two-variable model. This approach is continued until some stopping rule is satisfied.
    2. **Backward selection** : We start with all variables in the model, and remove the variable with the largest p-value—that is, the variable selection that is the least statistically significant. The new (p − 1)-variable model is fit, and the variable with the largest p-value is removed. This procedure continues until a stopping rule is reached. For instance, we may stop when all remaining variables have a p-value below some threshold.
    3. **Mixed selection.** : This is a combination of forward and backward selection. We start with no variables in the model, and as with forward selection selection, we add the variable that provides the best fit. We continue to add variables one-by-one. Of course, as we noted with the Advertising example, the p-values for variables can become larger as new predictors are added to the model. Hence, if at any point the p-value for one of the variables in the model rises above a certain threshold, then we remove that variable from the model. We continue to perform these forward and backward steps until all variables in the model have a sufficiently low p-value, and all variables outside the model would have a large p-value if added to the mode

3. Model Fit
	Two of the most common numerical measures of model fit are the RSE and R^2, the fraction of variance explained.
    In other words, there is a small increase in R2 if we include newspaper advertising in the model that already contains TV and radio advertising, even though we saw earlier that the p-value for newspaper advertising is not significant. It turns out that R2 will always increase when more variables are added to the model, even if those variables are only weakly associated with the response. This is due to the fact that adding another variable to the least squares equations must allow us to fit the training data (though not necessarily the testing data) more accurately. Thus, the R2 statistic, which is also computed on the training data, must increase. The fact that adding newspaper advertising to the model containing only TV and radio advertising leads to just a tiny increase in R2 provides additional evidence that newspaper can be dropped from the model. Essentially, newspaper provides no real improvement in the model fit to the training samples, and its inclusion will likely lead to poor results on independent test samples due to overfitting.
    
4. Predictions
	Confidence Intervals: Since least squares coefficients are prediction for the population coefficients assuming the linear modela assumption. Otherwise there is also model bias inovlved.
	Prediction Intervals : accounts the Irreducible error
    
#### Other Considerations in the Regression Model

###### Qualitative Predictors
In our discussion so far, we have assumed that all variables in our linear regression model are quantitative. But in practice, this is not necessarily the case; often some predictors are qualitative

**Predictors with Only Two Levels**

Create dummy variables

**Qualitative Predictors with More than Two Levels**

Create more dummy variables

###### Extensions of the Linear Model

The standard linear regression model provides interpretable results and works quite well on many real-world problems. However, it makes several highly restrictive assumptions that are often violated in practice. Two of the most important assumptions state that the relationship between the predictors and response are additive and linear. THe additive assumption means that the effect of changes in a predictor Xj on the response is independent of the values of the other predictors. The linear assumption states that the change in the response Y due to a one-unit change in Xj is constant, regardless of the value of Xj.

**Removing the Additive Assumption**

Interaction effect : Between two variables

The hierarchical principle states that if we include an interaction in a model, we should also include the main effects, even if the p-values associated with their coefficients are not significant.

However, the concept of interactions applies just as well to qualitative variables, or to a combination of quantitative and qualitative variables. In fact, an interaction between a qualitative variable and a quantitative variable has a particularly nice interpretation

**Non-linear Relationships**
In some cases, the true relationship between the response and the predictors may be nonlinear. Here we present a very simple way to directly extend the linear model to accommodate non-linear relationships, using polynomial regression.
 
Extending the linear model to accommodate non-linear relationships is known as polynomial regression, since we have included polynomial functions of the predictors in the regression model. 

###### Potential Problems

1. **Non-linearity of the Data**
	Residual plots are a useful graphical tool for identifying non-linearity.
2. **Correlation of Error Terms**
	Why might correlations among the error terms occur? Such correlations frequently occur in the context of time series data, which consists of observations for which measurements are obtained at discrete points in time. In many cases, observations that are obtained at adjacent time points will have positively correlated errors. In order to determine if this is the case for a given data set, we can plot the residuals from our model as a function of time. If the errors are uncorrelated, then there should be no discernible pattern. On the other hand, if the error terms are positively correlated, then we may see tracking in the residuals—that is, adjacent residuals may have similar values. 
    
3. **Non-constant Variance of Error Terms**
	Unfortunately, it is often the case that the variances of the error terms are non-constant. For instance, the variances of the error terms may increase with the value of the response. One can identify non-constant variances in the errors, or heteroscedasticity, from the presence of a funnel shape in heteroscedathe residual plot. 
    Sometimes we have a good idea of the variance of each response. Then we can use *Weighted least squares* - giving weights to each observation.
    
4. Outliers

	In practice, it can be difficult to decide how large a residual needs to be before we consider the point to be an outlier. To address this problem, instead of plotting the residuals, we can plot the studentized residuals, computed by dividing each residual ei by its estimated standard error. Observations whose studentized residuals are greater than 3 in absolute value are possible outliers.
    
5. 
