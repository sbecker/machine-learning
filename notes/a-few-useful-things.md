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

## 5. Overfitting has many faces

If knowledge and data are not sufficient to determine the correct classifier, we run the risk of hallucinating a classifier not grounded in reality, and is simply encoding random quirks in the data. This is called **overfitting**.

When your learner outputs a classifier that is 100% accurate on the training data but only 50% accurate on test data, when in fact it could have output one that is 75% accurate on both, it has overfit.

Generalization error can be decompsed into **bias** and **variance**.

**Bias** is a learner’s tendency to consistently learn the same wrong thing ~ underfitting

**Variance**  is the tendency to learn random things irrespective of the real signal ~ overfitting

Contrary to intuition, a more powerful learner is not necessarily better than a less powerful one.

Situations like this are common in machine learning: strong false assumptions can be better than weak true ones, because a learner with the latter needs more data to avoid overfitting.

### Methods to combat overfitting

1. Cross-validation can help to combat overfitting, but if we use it to make too many parameter choices it can itself start to overfit.

2. Adding a *regularization term* to the evaluation function. Can penalize classifiers with more structure, favoring smaller ones with less room to overfit.

3. perform a statistical significance test like chi-square before adding new structure, to decide whether the distribution of the class really is different with and without this structure

Be skeptical of claims that a particular technique “solves” the overfitting problem.

It's easy to avoid overfitting (variance) by falling into the opposite error of underfitting (bias).

Simultaneously avoiding both requires learning a perfect classifier, and short of knowing it in advance there is no single technique that will always do best (no free lunch).

Severe overfitting can occur even in the absence of noise. 

The problem of multiple testing.  What looks significant may in fact not be. Example: trend graph showing correlation between 
letters in winning word of spelling bee correlated with number of people killed by spiders - clear similarity in trends is a coincidence. If many data series are compared, similarly convincing but coincidental data may be obtained. [link](https://en.wikipedia.org/wiki/Multiple_comparisons_problem#/media/File:Spurious_correlations_-_spelling_bee_spiders.svg)

A mutual fund that beats the market ten years in a row looks very impressive, until you realize that, if there are 1000 funds and each has a 50% chance of beating the market on any given year, it’s quite likely that one will succeed all ten times just by luck.

Combat the problem by controlling the fraction of falsely accepted non-null hypotheses, known as the "false discovery rate".

## 6. Intuition fails in high dimensions
