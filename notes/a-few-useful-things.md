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

