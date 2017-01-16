# Linear Regression

An approach for modeling the relationship between a scalar dependent variable Y and 1-n explanatory (independent variables) X.

or

The task of fitting a single line through a scatter plot.

![scatterplot](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Linear_regression.svg/438px-Linear_regression.svg.png)

Unpacking it:
- Linear: The line is straight. The rate of change is constant.
- Regression Analysis: statistical process for estimating the relationships among variables

## Example Relationships, 

**X**: explanatory / independent variable, **Y**: dependent variable

- X = House Sq Feet, Y = sale price - as sq feet rises, so does sale price
- X = Height, Y = weight - as height rises, so does weight
- X = driving speed, Y = gas mileage - as driving speed increases, gas mileage decreases
- X = latitude at center of state, Y = rate of mortality due to skin cancer
- X = years of smoking packs of cigarettes, Y = vital lung capacity

## Math

Simplest form for with one dependent and one independent variable:

```
y = c + b*x
```

- y = estimated dependent
- c = constant
- b = regression coefficients
- x = dependent variable

For "simple" single variable linear regression we can use the standard `y = mx + b` line equation.

```
y = m*x + b
```

It's the same as above but you might recognize it from high school math class.

- y = y value of the line
- x = x value of the line
- m = the slope 
- b = the y intercept

In simple linear regression, we are trying to find the best slope (m) and y-intercept (b).

## Linear Regression Analysis

1. analyze correlation and directionality of data
2. estimate the model / fit the line
3. evaluate validity and usefulness of model

## How to measure line fit

1. Visually: plot the line on the scatter plot.
2. Measure the "error". The error is how far off the closest point on the line is from a given point in the dataset. Iterate through each x/y point in the dataset and sum the square distances between ecah point's y value and the candidate line's y value. (mx + b). This process is encapsulated in a **cost function**.

## How to optimize line fit

- Use [Gradient Descent](https://github.com/sbecker/machine-learning/blob/master/gradient-descent.md)!

## Resources
- [Wikipedia Article](https://en.wikipedia.org/wiki/Linear_regression)
- [Lesson 1: Simple Linear Regression | STAT 501](https://onlinecourses.science.psu.edu/stat501/node/250)
- [What is Linear Regression?](http://www.statisticssolutions.com/what-is-linear-regression/)
- [Regression Analysis](https://en.wikipedia.org/wiki/Regression_analysis)
- [Introduction to linear regression analysis]http://people.duke.edu/~rnau/regintro.htm
