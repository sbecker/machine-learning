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

You add the elements at each position. You can only add matrixes of the same size and shape:
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

| 1 2104 |   |  -40 |   |    486 | (-40x1 + 0.25x2104 = 486)
| 1 1416 | x | 0.25 | = |    314 | (-40x1 + 0.25x1416 = 314)
| 1 1534 |              |  343.5 | (-40x1 + 0.25x1534 = 343.5)
| 1 852  |              |    173 | (-40x1 + 0.25x852  = 173)
```

In a software library, this one line could look like
```
prediction = dataMatrix * parameters
```

## Matrix Matrix Multiplication

Multiply `m x n` matrix (m rows, n columns) by `n x o` matrix (n rows, o columns). Number of **columns** in **first** matrix must match the number of **rows** in the **second** matrix.
