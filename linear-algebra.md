# Linear Algebra & Matrix Math

## Definitions

- [Matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics)): A rectangular or two dimensional array of numbers
- Dimension of matrix: number of rows x number of columns

A 2 x 3 matrix:
```
| 1 2 3 |
| 4 5 6 |
```

- Vector: A N x 1 matrix, or a matrix with only one column

A 4 x 1 vector, or 4-dimensional vector:
```
| 1 |
| 3 |
| 4 |
| 9 |
```

## Matrix Addition

You add the elements at each position. You can only add matrices of the same size and shape:
```
| 1 0 |   | 4 0.5 |   | 5 0.5 |
| 2 5 | + | 2   5 | = | 4  10 |
| 3 1 |   | 0   1 |   | 3   2 |
```

## Scalar Multiplication
Multiply a single number by every element in a matrix.
```
    | 1 0 |   | 3  0 |
3 x | 2 5 | = | 6 15 |
    | 3 1 |   | 9  3 |
```

## Matrix Vector Multiplication
Multiply a matrix with m rows and n columns by a vector with n rows. Matrix must have same number of columns as vector has rows. Outputs a vector with same number of columns as the matrix had rows (m).

```
| 1 3 |   | 1 |   | 16 | (1x1 + 3x5 = 16)
| 4 0 | x | 5 | = |  4 | (4x1 + 0x5 = 4)
| 2 1 |           |  7 | (2x1 + 1x5 = 7)
```

**Trick for calculating all predicted values of a hypthesis in one line of code**

If hypothesis for predicting housing prices from square feet x is `hϴ = -40 x 0.25x` and house sq feet data set is `[2104, 1416, 1534, 852]`, we can do a matrix vector multiplication to calculate all predicted values at once:

```

| 1 2104 |   |  -40 |   | 486 | (-40x1 + 0.25x2104 = 486)
| 1 1416 | x | 0.25 | = | 314 | (-40x1 + 0.25x1416 = 314)
| 1 1534 |              | 344 | (-40x1 + 0.25x1534 = 343.5)
| 1 852  |              | 173 | (-40x1 + 0.25x852  = 173)
```

In a software library, this one line could look like
```
prediction = dataMatrix * parameters
```

## Matrix Matrix Multiplication

Multiply `m x n` matrix (m rows, n columns) A by `n x o` matrix (n rows, o columns) B. Number of **columns** in **first** matrix must match the number of **rows** in the **second** matrix. Output will be an `m x o` matrix C.

Process: Take every column of matrix B as a vector and multiply it by matrix A. Resulting vector becomes corresponding column in output matrix C.

**Trick for calculating all predicted values of many hyptheses at once, in one line of code**

```
  dataset       hϴ1 hϴ2  hϴ3        p1  p2  p3
| 1 2104 |   |  -40 200 -150 |   | 486 410 692 |
| 1 1416 | x | 0.25 0.1  0.4 | = | 314 342 416 |
| 1 1534 |                       | 344 353 464 |
| 1 852  |                       | 173 285 191 |
```

```
predictions = dataMatrix * parameters (of all hypthoses)
```

## Matrix Multiplication Properties

[Commutative property](https://en.wikipedia.org/wiki/Commutative_property): changing the order of the operands does not change the result.

Normal multiplication IS commutative: `3 x 2 == 2 x 3`

Assuming A and B are matrices, `A x B != B x A` - IS NOT commutative like normal matrix multiplication.

[Associative property](https://en.wikipedia.org/wiki/Associative_property): rearranging the parentheses in a multiplication will not change its value

Normal multiplication is associative: `2 x (3 x 4) == (2 x 3) x 4 = 24`

Matrix multiplication is associative: `A x (B x C) == (A x B) x C` 

# Resources

- [Coursera ML Class: Linear Algebra Review](https://www.coursera.org/learn/machine-learning/lecture/38jIT/matrices-and-vectors)
- [Deep Learning Book: Chapter 2: Linear Algebra](http://www.deeplearningbook.org/contents/linear_algebra.html)
- [Deep Learning Book: Lecture Slides](http://www.deeplearningbook.org/slides/02_linear_algebra.pdf)
- [Khan Academy: Jacobian prerequisite knowledge](https://www.khanacademy.org/math/multivariable-calculus/multivariable-derivatives/jacobian/v/jacobian-prerequisite-knowledge)

