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

After overfitting, the biggest problem in machine learning is the *curse of dimensionality*. [wikipedia](https://en.wikipedia.org/wiki/Curse_of_dimensionality)

Refers to various phenomena that arise when analyzing and organizing data in high-dimensional spaces (often with hundreds or thousands of dimensions) that do not occur in low-dimensional settings such as the three-dimensional physical space of everyday experience.

Translation: certain learning algorithms may perform poorly in high-dimensional data [link: quora](https://www.quora.com/What-is-the-curse-of-dimensionality)

Generalizing correctly becomes exponentially harder as the dimensionality (number of features) of the examples grows, because a fixed-size training set covers a dwindling fraction of the input space

More features = more combinations = smaller % of training data compared to possibilities

The similarity-based reasoning that machine learning algorithms depend on (explicitly or implicitly) breaks down in high dimensions

In high dimensions all examples look alike

Our intuitions, which come from a three-dimensional world, often do not apply in high-dimensional ones.

In high dimensions, most of the mass of a multivariate Gaussian distribution is not near the mean, but in an increasingly distant “shell” around it; most of the volume of a high-dimensional orange is in the skin, not the pulp.

Building a classifier in two or three dimensions is easy = can see whats going on by visual inspection.

In higher dimensions it's hard to understand whats happening - can't easily visualize it.

### Blessing of Non-uniformity

This effect partly counteracts the curse of dimensionality.

In most applications examples are not spread uniformly throughout the instance space, but are concentrated on or near a lower-dimensional manifold.

1. Learners can implicitly take advantage of this lower effective dimension
2. Algorithms for explicitly reducing the dimensionality can be used

## 7. Theoretical guarantees are not what they seem

Machine learning papers are full of theoretical guarantees.

Most common type: a bound on the number of examples needed to ensure good generalization

Conventional wisdom: in deduction you can guarantee conclusions are correct; in induction all bets are of

One of the major developments of recent decades has been the realization that in fact we can have guarantees on the results of induction, particularly if we’re willing to settle for probabilistic guarantees.

Guarantees of this type have to be taken with a large grain of salt.

Most interesting hypothesis spaces are doubly exponential in the number of features d, which still leaves us needing a number of examples exponential in d.

If there are 100 Boolean features and the hypothesis space is decision trees with up to 10 levels, to guarantee δ = ǫ = 1% in the bound above we need half a million examples. But in practice a small fraction of this suffices for accurate learning.

The main role of theoretical guarantees in machine learning is not as a criterion for practical decisions, but as a source of understanding and driving force for algorithm design.

The close interplay of theory and practice is one of the main reasons machine learning has made so much progress over the years. But caveat emptor: learning is a complex phenomenon, and just because a learner has a theoretical justification and works in practice doesn’t mean the former is the reason for the latter

## 8. Feature engineering is the key

Most important factor in success/failure of machine learning projects is the features used.
Typically where most of the effort in a machine learning project goes.
Intuition, creativity and “black art” are as important as the technical stuf

- many independent features that each correlate well with the class, learning is easy
- if the class is a very complex function of the features, you may not be able to learn it

Often, raw data is not in a form amenable to learning, but you can construct features from it that are.

Little time in a machine learning project is spent doing actual machine learning. 

More time is spent:
- gathering data
- integrating it
- cleaning it
- pre-process it
- trial and error of feature design

Machine learning projects are not a one-shot process of building a data set and running a learner, but rather an iterative
process of running the learner, analyzing the results, modifying the data and/or the learner, and repeating.

Feature engineering is more difficult because it’s domain-specific, while learners can be largely general-purpose.

The most useful learners are those that facilitate incorporating knowledge.

One of the holy grails of machine learning is to automate more and more of the feature engineering process.

Often done by generating large numbers of candidate features, selecting the best by information gain with respect to the class.

Features that look irrelevant in isolation may be relevant in combination.

There is ultimately no replacement for the smarts you put into feature engineering.

## 9. More data beats a cleverer algorithm

Pragmatically the quickest path to success is often to just get more data.

A rule of thumb: a dumb algorithm with lots and lots of data beats a clever one with modest amounts of it. 

Machine learning is all about letting data do the heavy lifting.

**Scalability**: In most of computer science, the two main limited resources are time and memory. In machine learning, there is a third one: training data.

- In the 1980s, limiting factor was data.
- Today it tends to be time. Lots of data, not enough time to process it, goes unused.

Paradox: even though in principle more data means that more complex classifiers can be learned, in practice simpler classifiers wind up being used, because complex ones take too long to learn.

Part of the reason using cleverer algorithms has a smaller payoff: at first approximation, they all do the same.

All learners essentially work by grouping nearby examples into the same class; the key difference is in the meaning of "nearby."

As a rule, it pays to try the simplest learners first (e.g., naive Bayes before logistic regression, k-nearest neighbor before support vector machines).

More sophisticated learners are seductive, but they are usually harder to use, because they have more knobs you need to turn to get good results, and because their internals are more opaque.

Learners can be divided into two major types
- those whose representation has a fixed size, like linear classifiers
- those whose representation can grow with the data, like decision trees.

Fixed-size learners can only take advantage of so much data.

Variable-size learners can in principle learn any function given sufficient data, but in practice they may not, because of limitations of the algorithm or computational cost.

Clever algorithms - those that make the most of the data and computing resources available—often pay off in the end, provided you’re willing to put in the effort.

Machine learning projects often wind up having a significant component of learner design, and practitioners need to have some expertise in it.

The biggest bottleneck is not data or CPU cycles, but human cycles. The human effort saved and insight gained, is often more important than accuracy and computational cost.

**The organizations that make the most of machine learning are those that have in place an infrastructure that makes experimenting with many different learners, data sources and learning problems easy and efficient, and where there is a close collaboration between machine learning experts and application domain ones.**

## 10. Learn many models, not just one

Early days of ML, everyone had their favorite learner. Then data showed the best learner varies from one application to another. Then researchers noticed if we combine many variations, the results are often much better, at little extra cost.

**Ensemble modeling** is the process of running two or more related but different analytical models and then synthesizing the results into a single score or spread in order to improve the accuracy of predictive analytics and data mining applications. [wikipedia](https://en.wikipedia.org/wiki/Ensemble_learning)

Ensemble modeling techniques

- **Bagging**: generate random variations of the training set by resampling, learn a classifier on each, and combine the results by voting. This works because it greatly reduces variance while only slightly increasing bias.

- **Boosting**: training examples have weights, and these are varied so that each new classifier focuses on the examples the previous ones tended to get wrong

- **Stacking**: outputs of individual classifiers become the inputs of a “higher-level” learner that figures out how best to combine them

The winner and runner up of the Netflix prize were both stacked ensembles of over 100 learners. Combining the two ensembles produced even better results.

Model ensembles should not be confused with Bayesian model averaging (BMA).

**Bayesian model averaging**:  the theoretically optimal approach to learning.  In BMA, predictions on new examples are made by averaging the individual predictions of all classifiers in the hypothesis space, weighted by how well the classifiers explain the training data and how much we believe in them *a priori.*

While model ensembles are a key part of the machine learning toolkit, BMA is seldom worth the trouble.

## 11. Simplicity does not imply accuracy
Occam’s razor famously states that entities should not be multiplied beyond necessity. [wikipedia](https://en.wikipedia.org/wiki/Occam's_razor) Simpler theories are preferable to more complex ones because they are more testable.

Assumption: given two classifiers with the same training error, the simpler of the two will likely have the lowest test error

Wrong: there are many counterexamples to it, and the “no free lunch” theorems imply it cannot be true

Examples
- model ensembles
- support vector machines: can effectively have an infi- nite number of parameters without overfitting

There is no necessary connection between the number of parameters of a model and its tendency to overfit

More sophisticated view instead equates complexity with the size of the hypothesis space.

Conclusion is that simpler hypotheses should be preferred because simplicity is a virtue in its own right, not because of a hypothetical connection with accuracy.

## 12. Representable does not imply learnable

Just because a function can be represented does not mean it can be learned.

Example:
- standard decision tree learners cannot learn trees with more leaves than there are training examples

The key question is not “Can it be represented?”, to which the answer is often trivial, but “Can it be learned?” And it pays to try different learners (and possibly combine them).

Using a representation with more layers (i.e., more steps between input and output), parity can be encoded in a linear-size classifier.

Finding methods to learn these deeper representations is one of the major research frontiers in machine learning..

## 13. Correlation does not imply causation

More often than not, the goal of learning predictive models is to use them as guides to action. 

A famous example in the world of data mining: If we find that beer and diapers are often bought together at the supermarket, then perhaps putting beer next to the diaper section will increase sales.

Machine learning is usually applied to *observational data*, where the predictive variables are not under the control of the learner, as opposed to *experimental data*, where they are

Practical points for machine learning:

- Whether or not we call them "causal," we would like to predict the effects of our actions, not just correlations between observable variables. 
- If you can obtain experimental data (for example by randomly assigning visitors to different versions of a Web site), then by all means do so.

## 14. Conclusion
ML has a lot of "folk wisdom" that can be hard to come by, but is crucial for success.

- A good place to learn more is my book The Master Algorithm, a non-technical introduction to machine learning.
- For a complete online machine learning course, check out http://www.cs.washington.edu/homes/pedrod/class
- There is also a treasure trove of machine learning lectures at http://www.videolectures.net
- A widely used open source machine learning toolkit is [Weka](http://www.cs.waikato.ac.nz/ml/weka/index.html)
