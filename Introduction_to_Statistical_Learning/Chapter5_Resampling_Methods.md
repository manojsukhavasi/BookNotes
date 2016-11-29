# Chapter 5 : Resampling methods

Resampling methods involve repeatedly drawing samples from a training set and refitting a model of interest on each sample in order to obtain additional information about the fitted model.

we discuss two of the most commonly used resampling methods, *cross-validation* and the *bootstrap*

**cross-validation** can be used to estimate the test error associated with a given statistical learning method in order to evaluate its performance, or to select the appropriate level of flexibility. The process of evaluating a model’s performance is known as model assessment, whereas the process of selecting the proper level of flexibility for a model is known as model selection.

**Bootstrap** is used in several contexts, most commonly to provide a measure of accuracy of a parameter estimate or of a given statistical learning method.

### Cross-Validation

##### The Validation Set Approach
Having one training set and one test set.

The validation estimate of the test error rate can be highly variable.
 
Statistical methods tend to perform worse when trained on fewer observations, this suggests that the validation set error rate may tend to overestimate the test error rate for the model fit on the entire data set.

##### Leave-One-Out Cross-Validation

The statistical learning method is fit on the n − 1 training examples and predicted on the remaining one example.

This provides an approximately unbiased estimate for the test error. But even though this is unbiased for the test error, it is a poor estimate because it is highly variable, since it is based upon a single observation.

This procedure can be repeated n times, leaving one example each time and then estimating test error as average of all errors.

LOOCV has a couple of major advantages over the validation set approach. First, it has far less bias. In LOOCV, we repeatedly fit the statistical learning method using training sets that contain n − 1 observations, almost as many as are in the entire data set. This is in contrast to the validation set approach, in which the training set is typically around half the size of the original data set. Consequently, the LOOCV approach tends not to overestimate the test error rate as much as the validation set approach does. Second, in contrast to the validation approach which will yield different results when applied repeatedly due to randomness in the training/validation set splits, performing LOOCV multiple times will always yield the same results: there is no randomness in the training/validation set splits.

READ THIS BIT LATER A BIT MORE ABOUT THE APPROXIMATION TO ERROR.

#####k-Fold Cross-Validation

This approach involves randomly dividing the set of observations into k groups, or folds, of approximately equal size.
The set of observations is divided into k groups, or folds, of approximately equal size. The first fold is treated as a validation set, and the method is fit on the remaining k − 1 folds. The error,is then computed on the observations in the held-out fold. This procedure is repeated k times and test error is approximated by the average of k errors.


When we perform cross-validation, our goal might be to determine how well a given statistical learning procedure can be expected to perform on independent data. But at other times we are interested only in the location of the minimum point in the estimated test MSE curve. This is because we might be performing cross-validation on a number of statistical learning methods, or on a single method using different levels of flexibility, in order to identify the method that results in the lowest test error. For this purpose, the location of the minimum point in the estimated test MSE curve is important, but the actual value of the estimated test MSE is not. We find in examples given that despite the fact that they sometimes underestimate the true test MSE, all of the CV curves come close to identifying the correct level of flexibility—that is, the flexibility level corresponding to the smallest test MSE.

##### Bias-Variance Trade-Off for k-Fold Cross-Validation

validation set approach can lead to overestimates of the test error rate, since in this approach the training set used to fit the statistical learning method contains only half the observations of the entire data set. Hence this suffers from bias. Using this logic, it is not hard to see that LOOCV will give approximately unbiased estimates of the test error, since each training set contains n − 1 observations, which is almost as many as the number of observations in the full data set. Therefore, from the perspective of bias reduction, it is clear that LOOCV is to be preferred to k-fold CV.



It turns out that LOOCV has higher variance than does k-fold CV with k < n. Why is this the case? When we perform LOOCV, we are in effect averaging the outputs of n fitted models, each of which is trained on an almost identical set of observations; therefore, these outputs are highly (positively) correlated with each other. In contrast, when we perform k-fold CV with k < n, we are averaging the outputs of k fitted models that are somewhat less correlated with each other, since the overlap between the training sets in each model is smaller. Since the mean of many highly correlated quantities has higher variance than does the mean of many quantities that are not as highly correlated, the test error estimate resulting from LOOCV tends to have higher variance than does the test error estimate resulting from k-fold CV.


##### Cross-Validation on Classification Problems

### The Bootstrap

The bootstrap is a widely applicable and extremely powerful statistical tool that can be used to quantify the uncertainty associated with a given estimator or statistical learning method.

The power of the bootstrap lies in the fact that it can be easily applied to a wide range of statistical learning methods, including some for which a measure of variability is otherwise difficult to obtain and is not automatically output by statistical software.

