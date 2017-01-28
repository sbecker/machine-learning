# Notes on: "A Few Useful Things to Know about Machine Learning"
http://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf

This article summarizes twelve key lessons that machine learning researchers and practitioners have learned.
- pitfalls to avoid
- important issues to focus on
- answers to common questions

## 1. Intro
much of the “folk knowledge” that is needed to successfully develop machine learning applications is not readily available in text books

Classifier: a system that inputs a vector of discrete or continuous *feature values* and outputs a single discrete value, the *class*.

Example: a vector of discrete or continuous *feature values*, the input *x*, and the discrete value, the *class*, *y*.

Learner: inputs a *training set* of *examples* and outputs a *classifier*

The test of the learner: whether this classifier produces the correct output *y* for future examples *x*

## 2. Learning = Representation + Evaluation + Learning

There are literally thousands of machine learning algorithms available, and hundreds more are published each year. 

The key is to realize that it consists of combinations of just three components:

**Representation**: A classifier must be represented in formal language a computer can handle. The representation of a learner dictates the set of classifiers it can possibly learn. This is called the *hypothesis space* of a learner. If a classifier is not within the hypotheses space it can't be learned.

**Evaluation**: An evaluation function is needed to distinguish good classifiers from bad. Also called an objective function or scoring function. Evaluation function used internally may differ from external one we want classifier to optimize.

**Optimization**: A method to search among the classifiers for the highest scoring one. The choice of optimization technique is key to the efficiency of the learner. Helps determine classifier produced if evaluation function has more than one optimum. New learners typically start with off the shelf optimizers and later replace them with custom-designed ones.

<a href="http://matroid.com/scaledml/slides/jeff.pdf" target="_blank"><img src="https://github.com/sbecker/machine-learning/blob/master/images/three-components-of-learning-algorithms.png?raw=true" alt="Three Components of Learning Algorithms" width="600" /></a>


- Not all combinations of the three components make sense.
- Discrete representations naturally go with combinatorial optimization
- Continuous representations ones with continuous optimization
- Many learners have both discrete and continuous components
- The day may not be far when every single possible combination has appeared in some learner

- Most textbooks are organized by representation. The other components are equally important.

## 3. It's generalization that counts

The fundamental goal of machine learning is to generalize beyond the examples in the training set.

The most common mistake among machine learning beginners is to test on the training data and have the illusion of success.

You need to keep training data and test data separate.

Set some of the data aside from the beginning, and only use it to test your chosen classifier at the very end, followed by
learning your final classifier on the whole data.

Can be mitigated by doing cross-validation.

**Cross-validation**: Randomly dividing data into subsets, holding out each while training on the rest, testing each learned classifier on the examples it didn't see, and averaging the results to see how well the parameter setting does.

## 4. Data alone is not enough

Every learner must embody some knowledge or assumptions beyond the data it’s given in order to generalize beyond it.

This was formalized by Wolpert in his famous “no free lunch” theorems, according to which no learner can beat random guessing over all possible functions to be learned.

Very general assumptions are often enough to do very well, and this is a large part of why machine learning has been so successful.

General assumptions
- smoothness
- similar examples having similar classes
- limited dependences
- limited complexity

One of the key criteria for choosing a representation is which kinds of knowledge are easily expressed in it.

If we have a lot of knowledge about...
- what makes examples similar in our domain, instance based methods may be a good choice.
- probabilistic dependencies, graphical models are a good fit.
- what kinds of preconditions are required by each class, “IF . . . THEN . . .” rules may be the the best option

Most useful learners are those that don’t just have assumptions hard-wired into them, but:
- allow us to state them explicitly
- vary them widely
- incorporate them automatically into the learning

Programming, like all engineering, is a lot of work: we have to build everything from scratch.

Learning is more like farming, which lets nature do most of the work. 

Farmers combine seeds with nutrients to grow crops. Learners combine knowledge with data to grow programs.

