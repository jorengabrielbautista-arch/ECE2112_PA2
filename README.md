### Joren Gabriel P. Bautista
### 2ECE-D

# ECE2112_PA2
## Purpose
  This README explains the various functions of the different lines of code that was used in this project.  

## A. REPRODUCIBLE NORMALIZATION PROBLEM

###   Description 
Create a reproducible random 5 × 5 integer ndarray named X.
Normalize the complete array by using: 
$$Z = \frac{X - \bar{x}}{\sigma}$$
    where \bar{x} is the mean of all 25 elements and σ is their population standard deviation as returned by
NumPy’s default std() call. 

### Repuirements
Required checks:

* Display $X$, $X_{\text{normalized}}$, its mean, and its standard deviation.
* Up to floating-point rounding:
  * The normalized mean must be 0
  * The normalized standard deviation must be 1
* Save the normalized array as: `X_normalized.npy`

### Full Code 
**`X_normalized.py`**
```python
np.random.seed(2112)
  X = np.random.randint(10, 101, size=(5, 5))

   x = np.mean(X)
 
      s = np.std(X)
  
          X_normalized = (X-x)/s
            X_normalized_mean = np.mean(X_normalized)
              X_normalized_std = np.std(X_normalized)

print ('X:\n', X)
print ('X_normalized: \n', X_normalized)
print ('X_normalized_mean: ', X_normalized_mean)
print ('X_normalized_std:', X_normalized_std)
      np.save ("X-normalized.npy", X_normalized)
```
#### Code Breakdown
```python
  np.random.seed(2112)
  X = np.random.randint(10, 101, size=(5, 5))
  X
```
> **Explanation:**  
>  This line of code sets up the 5 x 5 random matrix, which will have an output : 
 ```
array([[48, 11, 15, 67, 21],
       [11, 41, 13, 66, 24],
       [71, 79, 53, 67, 70],
       [77, 35, 91, 19, 96],
       [35, 54, 37, 41, 17]]) 
  ```
  
``` python
      x = np.mean(X)
      s = np.std(X)
```
> **Explanation:**  
> While the line above of code found above, takes the mean of the array and the standard deviation and assign it to *x* and *s* respectively



```python
X_normalized = (X - x) / s
X_normalized_mean = np.mean(X_normalized)
X_normalized_std = np.std(X_normalized)

```
> **Explanation:**  
> The first line executes this formula ($Z = \frac{X - \bar{x}}{\sigma}$) and assigns it to `X_normalized`.<br>
> The second and third lines take the mean and std of `X_normalized`.

```python
print ('X:\n', X)
print ('X_normalized: \n', X_normalized)
print ('X_normalized_mean: ', X_normalized_mean)
print ('X_normalized_std:', X_normalized_std)
```
  > **Explanation:**  
> * Prints the Array of X
> * Prints the Array of X_Normalized
> * Prints the mean of X_Normalized (0.0)
> * Prints the standard deviation of X_normalized (0.99999999999)
```python
 np.save ("X-normalized.npy", X_normalized)
```
 > **Explanation:**  
>And finally this saves the code as "X-normalized.npy"

## B. CUBES DIVISIBLE BY 4 PROBLEM

### Description

Create the first 100 positive integers, cube every element, and reshape the result into a $10 \times 10$ `ndarray` named $C$. Using a Boolean condition on $C$, extract every cubed value divisible by 4 while preserving NumPy's row-major order, and store the selected values in `div_by_4`.

### Requirements

* Display the shape of $C$, the array `div_by_4`, and the number of selected elements.
* Up to integer correctness:
* Exactly 50 elements must be selected.
* The first element must be 8 ($2^3$) and the last must be 1,000,000 ($100^3$).


* Save the selected array as: `div_by_4.npy`

### Full Code

**`div_by_4.py`**

```python
import numpy as np

integers = np.arange(1, 101)
C = (integers ** 3).reshape(10, 10)


div_by_4 = C[C % 4 == 0]

print("Shape of C:", C.shape)
print("div_by_4:\n", div_by_4)
print("Number of selected elements:", div_by_4.size)

# Save output array
np.save("div_by_4.npy", div_by_4)

```

#### Code Breakdown

```python
integers = np.arange(1, 101)
C = (integers ** 3).reshape(10, 10)

```

> **Explanation:**
> Creates an array of the first 100 positive integers ($1$ to $100$), raises every value to the third power ($x^3$), and reshapes the array into a $10 \times 10$ matrix named $C$.

```python
div_by_4 = C[C % 4 == 0]

```

> **Explanation:**
> Applies a Boolean check to evaluate each element's divisibility by 4 (`C % 4 == 0`). It selects all values that are divisible by 4 and assigns them to `div_by_4`.

```python
print("Shape of C:", C.shape)
print("div_by_4:\n", div_by_4)
print("Number of selected elements:", div_by_4.size)

```

> **Explanation:**
> * Displays the array $C$
> * prints the filtered array `div_by_4`, showing only the numbers divisible by 4
> * Outputs the total count of filtered elements (50).

```python
np.save("div_by_4.npy", div_by_4)

```

> **Explanation:**
> Saves the code to be a file named `div_by_4.npy`.

---

## C. ABOVE-MEAN SQUARES PROBLEM

### Description

Create a $6 \times 6$ `ndarray` named $S$ containing the squares of the first 36 positive integers in increasing row-major order. Compute the population mean of all elements in $S$, denoted as $S_{\text{mean}}$. Then, perform Boolean filtering to select all elements strictly greater than $S_{\text{mean}}$ and store them in `above_mean`.

### Requirements

* Display $S$, $S_{\text{mean}}$, `above_mean`, and the number of selected elements.
* Up to floating-point and integer correctness:
* Exactly 15 elements must be selected.
* The first element must be 484 ($22^2$) and the last must be 1296 ($36^2$).
* Save the selected array as: `above_mean.npy`

### Full Code

**`above_mean.py`**

```python
import numpy as np


integers = np.arange(1, 37)
S = (integers ** 2).reshape(6, 6)


S_mean = np.mean(S)
above_mean = S[S > S_mean]


print("S:\n", S)
print("S_mean:", S_mean)
print("above_mean:\n", above_mean)
print("Number of elements above mean:", above_mean.size)


np.save("above_mean.npy", above_mean)

```

#### Code Breakdown

```python
integers = np.arange(1, 37)
S = (integers ** 2).reshape(6, 6)

```

> **Explanation:**
> Generates numbers from 1 to 36, computes their squares ($x^2$), and reshapes the sequence into a $6 \times 6$ matrix named $S$.

```python
S_mean = np.mean(S)
above_mean = S[S > S_mean]

```

> **Explanation:**
> Computes the overall  mean of all 36 elements in $S$ and stores it in `S_mean`. Then applies Boolean condition (`S > S_mean`) to extract the elements that are greater than the mean into `above_mean`.

```python
print("S:\n", S)
print("S_mean:", S_mean)
print("above_mean:\n", above_mean)
print("Number of elements above mean:", above_mean.size)

```

> **Explanation:**
> *Prints the $6 \times 6$ matrix $S$
> *The calculated mean value $S_{\text{mean}}$
> *The resulting array of `above_mean`,
> *The total count of filtered elements (15).

```python
np.save("above_mean.npy", above_mean)

```

> **Explanation:**
> Finally saves the code to a file named `above_mean.npy`.
