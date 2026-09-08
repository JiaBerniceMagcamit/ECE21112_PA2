# ECE2112 PA 2
## Submitted by: Jia Bernice C. Magcamit
## Section: 2ECE-A

The content of this repository contains the Programming Assignment 2 for **ECE2112: Advanced Programming and Algorithms.** It has 3 Python programming problems covering Module 2: Numerical Python (NumPy).

## Objective

The objectives of this experiment are the following:

1. Build and reshape NumPy arrays using core built-in functions.
2. Perform efficient, element-wise mathematical operations directly on `ndarray` objects
3. Calculate key summary statistics and isolate specific elements using Boolean indexing
4. Save processed array data to disk using standard `.npy` file formats.

## Discussion and Analysis
### A. Reproducible Normalization Problem

This problem requires a reproducible random 5x5 integer ndarray named X, and to use the following statements before performing any calculation:

```
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```
and to normalize the array using:

`X_normalized = (X - x_mean) / x_std`

and to save the normalized array as:

`X_normalized.npy`

### CODE:

```
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

X_normalized = (X - x_mean) / x_std

np.save("X_normalized.npy", X_normalized)
data = np.load("X_normalized.npy")

print("X: \n", X)
print("\nX_normalized: \n", data)
print("\n Mean of X_normalized: \n", X_normalized.mean())
print("\n Standard Deviation of X_normalized: \n",X_normalized.std())

```
### OUTPUT: 

```
X: 
 [[48 11 15 67 21]
 [11 41 13 66 24]
 [71 79 53 67 70]
 [77 35 91 19 96]
 [35 54 37 41 17]]

X_normalized: 
 [[ 0.06340841 -1.36714726 -1.2124926   0.79801809 -0.98051059]
 [-1.36714726 -0.20723725 -1.28981993  0.75935442 -0.86451959]
 [ 0.95267275  1.26198209  0.25672675  0.79801809  0.91400909]
 [ 1.18465476 -0.43921926  1.72594609 -1.05783793  1.91926443]
 [-0.43921926  0.29539042 -0.36189192 -0.20723725 -1.13516526]]

 Mean of X_normalized: 
 0.0

 Standard Deviation of X_normalized: 
 0.9999999999999999
 ```
Using the functions `np.mean` and `np.std` and assigning them to variables, we can get the mean and standard deviation of the array X. The array X is then normalized using the formula above, and its array is now saved in `X_normalized.npy`, and the `np.load()` function is used to load the array data stored in the npy file.


### B. Cubes Divisible by 4 Problem

Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named C. Thus, C begins with 1^3 and ends with 100^3

Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in div by 4. Preserve NumPy’s normal row-major selection order.

The selected array should be saved as `div_by_4.npy`

### CODE:

```
integers = np.arange(1,101)
C = (integers**3).reshape(10,10)

div_by_4 = C[C%4 == 0]
np.save("div_by_4.npy", div_by_4)
div4 = np.load("div_by_4.npy")

print("Shape of C: \n", C.shape)
print("\n div_by_4: \n", div4)
print("\n Number of Selected Eleemnts: \n", div_by_4.size)

```

### OUTPUT:

```
Shape of C: 
 (10, 10)

 div_by_4: 
 [      8      64     216     512    1000    1728    2744    4096    5832
    8000   10648   13824   17576   21952   27000   32768   39304   46656
   54872   64000   74088   85184   97336  110592  125000  140608  157464
  175616  195112  216000  238328  262144  287496  314432  343000  373248
  405224  438976  474552  512000  551368  592704  636056  681472  729000
  778688  830584  884736  941192 1000000]

 Number of Selected Elements: 
 50

 ```

The function `np.arange` was used to generate the first 100 integers, which were later assigned to C, where all elements of the array were raised to the power of 3, and the array was reshaped into a 10x10 ndarray.

A Boolean condition is stored in the variable `div_by_4`, so it only generates all the cubed elements that are divisible by 4. The elements in div_by_4 are loaded using the `np.load()` function.


### C. Above-Mean Squares Problem

For this problem, a 6x6 ndarray named S should generate the first 3 positive integers in increasing row-major order. Then, compute the mean of all elements of S and store it in S mean. Then use Boolean filtering to select only the elements strictly greater than S mean. Store these values in above mean.

The selected array should be saved as `above_mean.npy`

### CODE 

```
S1 = np.arange(1,37)**2
S = S1.reshape(6,6)

S_mean = np.mean(S)
above_mean = S[S>S_mean]
np.save("above_mean.npy", above_mean)
abvmean = np.load("above_mean.npy")

print("S: \n", S)
print("\n S_mean: \n", S_mean)
print("\n above_mean: \n", abvmean)
print("\n Number of selected elements \n", above_mean.size)

```

### OUTPUT

```
S: 
 [[   1    4    9   16   25   36]
 [  49   64   81  100  121  144]
 [ 169  196  225  256  289  324]
 [ 361  400  441  484  529  576]
 [ 625  676  729  784  841  900]
 [ 961 1024 1089 1156 1225 1296]]

 S_mean: 
 450.1666666666667

 above_mean: 
 [ 484  529  576  625  676  729  784  841  900  961 1024 1089 1156 1225
 1296]

 Number of selected elements 
 15

 ```
The function `np.arange` was used to generate the first 36 integers, which were then squared. Then the array is assigned to S, where it was reshaped to become a 6x6 ndarray.

`np.mean()` was used to get the mean of S, then the variable above_mean was used to store a boolean condition

 