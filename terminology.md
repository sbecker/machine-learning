# Terminology

Notes on some of the basic concepts of machine learning, to clarify and reinforce my own understanding.

- [Linear Regression](https://github.com/sbecker/machine-learning/blob/master/linear-regression.md)
- [Gradient Descent](https://github.com/sbecker/machine-learning/blob/master/gradient-descent.md)
- Stochastic Gradient Descent: Incremental gradient descent - using small batches of random training data at each training step. much faster and more memory efficient. [wikipedia](https://en.wikipedia.org/wiki/Stochastic_gradient_descent)
- [Linear Algebra](https://github.com/sbecker/machine-learning/blob/master/linear-algebra.md)
- Logistic Regression: Used for binary classification problems - yes or no / is it A or B, etc. uses a sigmoid function (output looks like a big S), snap values to either 0 or 1 output depending on input range.
- [Kalman Filter](https://github.com/sbecker/machine-learning/blob/master/kalman-filter.md)

- Softmax (multinomial logistic) regression - two steps - first we add up the evidence of our input being in certain classes, and then we convert that evidence into probabilities. http://neuralnetworksanddeeplearning.com/chap3.html#softmax
- Parametric ML algorithms: learning models with a fixed-size set of parameters, independent of number of training examples. Generally have a high bias, fast to learn, easier to understand, less flexible. Lower predictive performance on complex problems do not meet simplifying assumptions of the algorithm's bias. [article](http://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)
- Nonparametric ML algorithms: good when lots of data and no prior knowledge. they do not make strong assumptions about the form of the mapping function [article](http://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)
- Bias: how well the model fits the data. low bias = closer to truth, high bias = farther from truth. simplifying assumptions made by a model to make the target function easier to learn
- Variance: how much the model changes based on changes in the inputs. the amount that the estimate of the target function will change if different training data was used
- Bias-Variance Trade-Off: The parameterization of machine learning algorithms is often a battle to balance out bias and variance. Increasing the bias will decrease the variance, Increasing the variance will decrease the bias. The best model usually lies in the middle. [article](http://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/)
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
- Multilayer Perceptron (MLP): a mathematical function mapping some set of input values to output values (DL Book). A feedforward artificial neural network model that maps sets of input data onto a set of appropriate outputs. An MLP consists of multiple layers of nodes in a directed graph, with each layer fully connected to the next one. [Wikipedia](https://en.wikipedia.org/wiki/Multilayer_perceptron)
- Weight / Synaptic Weight: the strength or amplitude of a connection between two nodes [wikipedia](https://en.wikipedia.org/wiki/Synaptic_weight)
- Node: a neuron (or processing element) with a nonlinear activation function
- Fit: Fitting a model is the process of learning the parameters of a model using training data
- Overfit: 
- Hyperparameter: "higher-level" parameters that cannot be learned from the data. define properties of the models, such as model complexity or learning rate
- Box-Cox transformation: a generalized "power transformation" that transforms data to make the distribution more normal
- LDA: Latent Dirichlet Allocation - a common method of topic modeling, or classifying documents by subject matter. a generative model that represents documents as a mixture of topics that each have their own probability distribution of possible words. documents are distributions of topics that are distributions of words.
- "Dirichlet" distribution: a distribution of distributions

- Dendogram: a tree diagram
- Hierarchical cluster models: distance-based models that represent clusters using dendrograms. They do not provide a single partition of the dataset, but instead produce a hierarchy of clusters that merge at certain distances.

- ROC Curve: receiver operating characteristic - the performance plot for binary classifiers of True Positive Rate (y-axis) vs. False Positive Rate (x-axis)
- AUC / AUROC: is area under the ROC curve. a common performance metric for evaluating binary classification models. better than raw accuracy. Used to class imbalance, unlike raw accuracy. For example, if just measuring on raw accuracy, when building a model to detect cancer that exists in 1% of population, you can achieve 99% accuracy by building a model that simply classifies everyone as cancer-free.

- Ensemble Learning: Combining multiple models for better performance
- Bagging / Bootstrap Aggregating: dataset is first divided into multiple subsets through resampling, then each subset is used to train a model, and the final predictions are made through voting or averaging the component models. computed in parallel.


## To Define

- Evidence

- Linear Discriminant Analysis
- Learning Vector Quantization
- K-Nearest Neighbors
- Support Vector Machines
- Bagging
- Random Forest
- Boosting
- AdaBoost
(see http://machinelearningmastery.com/machine-learning-algorithms-mini-course/ for some descriptions)

- Naive Bayes
- Directed Graph
- Feedforward
- Neural Network
- Covariance Matrix


- Winsorize
- PCA
- ICA

- Dimensionality reduction

- RELU: Rectified Linear Unit
- Learning Rate Decay
- Dropout

## Articles to Comb for terms
TODO: Comb through these articles and define all vague or unknown terms
- [Networks, Manifolds, and Topology](http://colah.github.io/posts/2014-03-NN-Manifolds-Topology/)
