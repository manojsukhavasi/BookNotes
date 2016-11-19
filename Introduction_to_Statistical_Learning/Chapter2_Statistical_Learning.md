## Chapter 2 : Statistical Learning

#### What is Statistical Learning

In essence, statistical learning refers to a set of approaches for estimating f.
In this chapter we outline some of the key theoretical concepts that arise in estimating f, as well as tools for evaluating the estimates obtained.

###### Why estimate f?
- Prediction
	- The accuracy of y as a prediction for Y depends on two quantities,which we will call the reducible error and the irreducible error
	- In general f will not be a perfect estimate for F, and this inaccuracy will introduce some error. This error is reducible because we can potentially improve the accuracy of f by using the most appropriate statistical learning technique to estimate F.
	- Irreducible error is due to non-availability of features. No model can capture with lack of features.
- Inference
	- In this situation we wish to estimate f, but our goal is not necessarily to make predictions for Y . We instead want to understand the relationship between X and Y


Depending on whether our ultimate goal is prediction, inference, or a combination of the two, different methods for estimating f may be appropriate. For example, linear models allow for relatively simple and interlinear model pretable inference, but may not yield as accurate predictions as some other approaches. In contrast, some of the highly non-linear approaches that we discuss in the later chapters of this book can potentially provide quite accurate predictions for Y , but this comes at the expense of a less interpretablemodel for which inference is more challenging.

###### How do we estimate f?
- Throughout this book, we explore many linear and non-linear approaches for estimating f
- Broadly speaking, most statistical learning methods for this task can be characterized as either parametric or non-parametric
	- **Parametric Methods**
    	- Parametric methods involve a two-step model-based approach.
    	- First, we make an assumption about the functional form, or shape, of f
    	- After a model has been selected, we need a procedure that uses the training data to fit or train the model
    	- it reduces the problem of estimating f down to one of estimating a set of parameters.
    	- The potential disadvantage of a parametric approach is that the model we choose will usually not match the true unknown form of f
	- **Non-parametric Methods**
		- Non-parametric methods do not make explicit assumptions about the functional form of f
		- since they do not reduce the problem of estimating f to a small number of parameters, a very large number of observations is required in order to obtain an accurate estimate for f

###### The Trade-Off Between Prediction Accuracy and Model Interpretability
why would we ever choose to use a more restrictive method instead of a very flexible approach?

There are several reasons that we might prefer a more restrictive model. If we are mainly interested in inference, then restrictive models are much more interpretable. For instance, when inference is the goal, the linear model may be a good choice since it will be quite easy to understand the relationship between Y and X

We have established that when inference is the goal, there are clear advantages to using simple and relatively inflexible statistical learning methods. In some settings, however, we are only interested in prediction, and the interpretability of the predictive model is simply not of interest.

###### Supervised Versus Unsupervised Learning

Most statistical learning problems fall into one of two categories: supervised or unsupervised.

###### Regression Versus Classification Problems

We tend to refer to problems with a quantitative response as regression problems, while those involving a qualitative response are often referred to as classification problems.

#### Assessing Model Accuracy

Selecting the best approach can be one of the most challenging parts of performing statistical learning in practice.

###### Measuring the Quality of Fit

In order to evaluate the performance of a statistical learning method on a given data set, we need some way to measure how well its predictions actually match the observed data. That is, we need to quantify the extent to which the predicted response value for a given observation is close to the true response value for that observation

we are interested in the accuracy of the predictions that we obtain when we apply our method to previously unseen test data.

As the flexibility of the statistical learning method increases, we observe a monotone decrease in the training MSE and a U-shape in the test MSE. This is a fundamental property of statistical learning that holds regardless of the particular data set at hand and regardless of the statistical method being used. As model flexibility increases, training MSE will decrease, but the test MSE may not. When a given method yields a small training MSE but a large test MSE, we are said to be overfitting the data.

Note that regardless of whether or not overfitting has occurred, we almost always expect the training MSE to be smaller than the test MSE because most statistical learning methods either directly or indirectly seek to minimize the training MSE. Overfitting refers specifically to the case in which a less flexible model would have yielded a smaller test MSE.

###### The Bias-Variance Trade-Off

It is possible to show that the expected test MSE, for a given value x0, can always be decomposed into the sum of three fundamental quantities: the variance of f(x0), the squared bias of f(x0) and the variance of the error variance terms.

In order to minimize the expected test error, we need to select a statistical learning method that simultaneously achieves low variance and low bias.

What do we mean by the variance and bias of a statistical learning method?
- Variance refers to the amount by which f would change if we estimated it using a different training data set. Since the training data are used to fit the statistical learning method, different training data sets will result in a different f ˆ. But ideally the estimate for f should not vary too much between training sets. However, if a method has high variance then small changes in the training data can result in large changes in f. In general, more flexible statistical methods have higher variance. 
- Bias refers to the error that is introduced by approximating a real-life problem, which may be extremely complicated, by a much simpler model. Generally, more flexible methods result in less bias.
- As a general rule, as we use more flexible methods, the variance will increase and the bias will decrease. 

###### The Classification Setting

- [ ] **The Bayes Classifier**
- Didn't clearly get the idea. Go through it again
- Bayes Decision boundary
- The Bayes classifier produces the lowest possible test error rate, called the Bayes error rate.
- The Bayes error rate is analogous to the irreducible error, discussed earlier

**K-Nearest Negihbours**

In theory we would always like to predict qualitative responses using the
Bayes classifier. But for real data, we do not know the conditional distribution of Y given X, and so computing the Bayes classifier is impossible. Therefore, the Bayes classifier serves as an unattainable gold standard against which to compare other methods. Many approaches attempt to estimate the conditional distribution of Y given X, and then classify a given observation to the class with highest estimated probability.

One such method is the K-nearest neighbors (KNN) classifier. Given a positive integer K and a test observation x0, the KNN classifier first identifies the neighbors K points in the training data that are closest to x0.

Despite the fact that it is a very simple approach, KNN can often produce classifiers that are surprisingly close to the optimal Bayes classifier.
    