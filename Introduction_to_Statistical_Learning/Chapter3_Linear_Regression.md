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

