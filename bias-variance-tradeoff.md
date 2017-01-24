# Bias-Variance Tradeoff

The parameterization of machine learning algorithms is often a battle to balance out bias and variance. Increasing the bias will decrease the variance, Increasing the variance will decrease the bias. The best model usually lies in the middle.

<img src="https://raw.githubusercontent.com/sbecker/machine-learning/master/images/bias-variance-dartboard.png" alt="Bias and variance in dart-throwing" width="500" /><br>
**Bias and variance in dart-throwing**

**Bias**:
- a learner’s tendency to consistently learn the same wrong thing
- how well the model fits the data
- simplifying assumptions made by a model to make the target function easier to learn
- low bias = closer to truth, high bias = farther from truth. 

**Variance**:
- the tendency to learn random things irrespective of the real signal
- how much the model changes based on changes in the inputs
- the amount that the estimate of the target function will change if different training data was used

## References
- [A Few Useful Things to Know about Machine Learning](http://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf)
- [Gentle Introduction to the Bias-Variance Trade-Off in Machine Learning](http://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/)
