# Terminology

Notes on some of the basic concepts of machine learning, to clarify and reinforce my own understanding.

- [Linear Regression](https://github.com/sbecker/machine-learning/blob/master/linear-regression.md)
- [Gradient Descent](https://github.com/sbecker/machine-learning/blob/master/gradient-descent.md)
- Stochastic Gradient Descent: Incremental gradient descent - using small batches of random training data at each training step [wikipedia](https://en.wikipedia.org/wiki/Stochastic_gradient_descent)
- [Linear Algebra](https://github.com/sbecker/machine-learning/blob/master/linear-algebra.md)
- Logistic Regression: Used for binary classification problems - yes or no / is it A or B, etc. uses a sigmoid function (output looks like a big S), snap values to either 0 or 1 output depending on input range.


- Softmax (multinomial logistic) regression - two steps - first we add up the evidence of our input being in certain classes, and then we convert that evidence into probabilities. http://neuralnetworksanddeeplearning.com/chap3.html#softmax
- Parametric ML algorithms: learning models with a fixed-size set of parameters, independent of number of training examples. Generally have a high bias, fast to learn, easier to understand, less flexible. Lower predictive performance on complex problems do not meet simplifying assumptions of the algorithm's bias. [article](http://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)
- Nonparametric ML algorithms: good when lots of data and no prior knowledge. they do not make strong assumptions about the form of the mapping function [article](http://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)
- Bias: simplifying assumptions made by a model to make the target function easier to learn
- Variance: the amount that the estimate of the target function will change if different training data was used
- Bias-Variance Trade-Off: The parameterization of machine learning algorithms is often a battle to balance out bias and variance. Increasing the bias will decrease the variance, Increasing the variance will decrease the bias. [article](http://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/)
- Activation / Link / Transfer function: defines the output of a node, given the input. called a transfer function in neural networks
- Topology: concerned with the properties of space that are preserved under continuous deformations, such as stretching and bending, but not tearing or gluing. [Wikipedia](https://en.wikipedia.org/wiki/Topology)
- Manifold: a topological space that locally resembles Euclidean space near each point [Wikipedia](https://en.wikipedia.org/wiki/Manifold)
- Training Data: the dataset used to train a supervised machine learning algorithm, and show it correct answers
- Test Data: the dataset used to test the accuracy of a machine learning algorithm, correct answer is not given
- Label: the answer, or assigned value for a given training example
- Vector: A N x 1 matrix, or a matrix with only one column, or 1 X N matrix with only one row
- Tensor: n-dimensional array
- One-hot vector: a vector which is 0 in most dimensions, and 1 in a single dimension
- Cost or Loss function: represents how far off our model is from our desired outcome
- Cross-entropy - measuring how inefficient our predictions are for describing the truth, or - the average length of communicating an event from one distribution with the optimal code for another distribution
- Logit: The logit function is the inverse of the inverse of the sigmoidal "logistic" function [Wikipedia](https://en.wikipedia.org/wiki/Logit)
- Backpropogation: reverse-mode differentiation, a technique for calculating derivatives quickly [visual explanation](http://colah.github.io/posts/2015-08-Backprop/) | [Book Chapter Explanation](http://neuralnetworksanddeeplearning.com/chap2.html) | [Wikipedia](https://en.wikipedia.org/wiki/Backpropagation)

## To Define

- Evidence
- Weights

- Linear Discriminant Analysis
- Learning Vector Quantization
- K-Nearest Neighbors
- Support Vector Machines
- Bagging
- Random Forest
- Boosting
- AdaBoost
(see http://machinelearningmastery.com/machine-learning-algorithms-mini-course/ for some descriptions)



## Articles to Comb for terms
TODO: Comb through these articles and define all vague or unknown terms
- [21 Must-Know Machine Learning Interview Questions and Answers](https://elitedatascience.com/machine-learning-interview-questions-answers)
- [Neural Networks, Manifolds, and Topology](http://colah.github.io/posts/2014-03-NN-Manifolds-Topology/)
