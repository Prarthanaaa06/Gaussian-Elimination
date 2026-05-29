# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
 1. Read and InitializeRead the number of unknowns ($n$).Read the coefficients into an augmented matrix $A$ of size $n \times (n+1)$, and initialize a solution array $X$ of size $n$.
 2. Forward Elimination (Row Echelon Form)Loop through each row $i$ from $0$ to $n-1$. If the diagonal element $A[i][i]$ is zero, stop (division by zero error).For every row $j$ below $i$, calculate a factor:$$\text{ratio} = \frac{A[j][i]}{A[i][i]}$$Subtract $\text{ratio} \times (\text{Row } i)$ from $\text{Row } j$ to eliminate the elements below the pivot.
 3. Back SubstitutionStart from the very last variable and solve directly:$$X[n-1] = \frac{A[n-1][n]}{A[n-1][n-1]}$$Work backward from row $n-2$ down to $0$. For each row $i$, subtract the known $X$ values multiplied by their coefficients from the constant term, and divide by the diagonal element $A[i][i]$.
 4. Output ResultsLoop through the array $X$ and print each calculated value formatted to your required precision (e.g., X0 = 53.35, X1 = -8.88).

## Program:
```
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: PRARTHANA D
RegisterNumber: 212225230213

import os
os.environ['OPENBLAS_NUM_THREADS'] = '1'
import numpy as np
import sys
n=int(input())
a=np.zeros((n,n+1))
x=np.zeros(n)
for i in range(n):
    for j in range(n+1):
        a[i][j]=float(input())
for i in range(n):
    if a[i][i]==0.0:
        sys.exit('Divide by zero detected!')
    for j in range(i+1,n):
        ratio=a[j][i]/a[i][i]
        for k in range(n+1):
            a[j][k]=a[j][k]-ratio*a[i][k]
x[n-1]=a[n-1][n]/a[n-1][n-1]
for i in range(n-2,-1,-1):
    x[i]=a[i][n]
    for j in range(i+1,n):
        x[i]=x[i]-a[i][j]*x[j]
    x[i]=x[i]/a[i][i]
for i in range(n):
    print('X%d = %0.2f '%(i,x[i]),end='')
*/
```

## Output:
<img width="1178" height="668" alt="image" src="https://github.com/user-attachments/assets/5d8ef523-effe-4595-9b5a-b4610d958dee" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

