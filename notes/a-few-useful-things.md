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
