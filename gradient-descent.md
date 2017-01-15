# Gradient Descent

Gradient Descent is an optimization algorithm. It "minimizes" functions. Given a function with a defined set of parameters, gradient descent starts with an initial set of values and moves towars parameter values that minimize the function.

![Gradient Descent](https://raw.githubusercontent.com/sbecker/machine-learning/master/images/gradient-descent.png)

This is a visualization of gradient descent. The landscape above is a depiction of many possible solutions for a simple linear regression problem. The altitude indicates the error rate. The lower the better. The lines chart the process of gradient descent. It starts from any given point, and takes steps down the slope until it finds a local minimum, where it can no longer descend.

# How it works

For simple, single variable linear regression:

1. Make a guess - pick some random starting point for the parameter values for drawing the straight line.
2. Measure error for all points in the dataset using the cost function.
3. Make another guess - slightly modify the parameter values, and redraw the line
4. Measure the error again.
5. Measure the difference in error from the first guess to the second. Did it get better or worse? Now you've determined a direction to move the parameter values. Use this info on next guess.
6. Repeat steps 3 to 5 to keep guessing values until the difference in error between guesses goes to zero.

There's also a process in here of measuring the slope of the error change (partial calculus derivatives, yay!) for determining direction to go, so the above is not quite accurate yet, but it's close.

## Links

- [Wikipedia Article](https://en.wikipedia.org/wiki/Gradient_descent)
- [An Introduction to Gradient Descent and Linear Regression](https://spin.atomicobject.com/2014/06/24/gradient-descent-linear-regression/)
