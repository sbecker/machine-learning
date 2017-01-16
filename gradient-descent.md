# Gradient Descent

Gradient Descent is an optimization algorithm. It "minimizes" functions. Given a function with a defined set of parameters, gradient descent starts with an initial set of values and moves towards parameter values that minimize the function.

![Gradient Descent](https://raw.githubusercontent.com/sbecker/machine-learning/master/images/gradient-descent.png)

This is a visualization of gradient descent. The landscape above is a depiction of many possible solutions for a simple linear regression problem. The altitude indicates the error rate. The lower the better. The lines chart the process of gradient descent. It starts from any given point, and takes steps down the slope until it finds a local minimum, where it can no longer descend.

## Unpacking It

- [Gradient](https://en.wikipedia.org/wiki/Gradient) - represents the slope of the tangent of the graph of the function. A generalization of the usual concept of derivative to functions of several variables.
- Descent - the function iterates to a local minimum by taking descending steps

# How it works

For simple, single variable linear regression:

1. Make a guess - pick some random starting point for the parameter values for drawing the straight line.
2. Measure error for all points in the dataset using the cost function.
3. Make another guess - slightly modify the parameter values, and redraw the line
4. Measure the error again.
5. Measure the difference in error from the first guess to the second. Did it get better or worse? Now you've determined a direction to move the parameter values. Use this info on next guess.
6. Repeat steps 3 to 5 to keep guessing values until the difference in error between guesses goes to zero.

There's also a process in here of measuring the slope of the error change (partial calculus derivatives, yay!) for determining direction to go, so the above is not quite accurate yet, but it's close.

## Other Terms

- Theta - ϴ - the parameters of the model. Broken out into ϴ0, ϴ1, .... ϴi
- Hypothesis - The linear regression line function (or more complex one) with a given set of ϴ parameter values plugged in. `hϴ(x) = ϴ0 + ϴ1x`, Shorthand `h(x)`
- Alpha - α - the learning rate - determines size of each step
- Cost Function: Measures the error between the hypothesis and the actual data. Takes an average difference of all results of the hypothesis with inputs from x’s and the actual output y’s. Also called the "squared error function" or "mean squared error". There are other cost functions but this is most common for regression problems.
- “Batch” gradient descent: at every step we look at all of the training examples

## Fixed learning rate != fixed step size

Gradient descent can converge to a local minimum, even with the learning rate α is fixed. As we approach the local minimum, (the slope/tangent/derivative decreases, so) gradient descent will automatically take smaller steps. So need to decrease α over time.

Failure to converge or too much time to obtain the minimum value imply that our step size is too large.

## Links

- [Wikipedia Article](https://en.wikipedia.org/wiki/Gradient_descent)
- [An Introduction to Gradient Descent and Linear Regression](https://spin.atomicobject.com/2014/06/24/gradient-descent-linear-regression/)
