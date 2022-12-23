﻿# Code：在线计算单位矩阵

### 在线调试环境1

- 单击右方的[pythontutor](https://pythontutor.com/visualize.html#mode=edit)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这段python代码拷贝到这个页面中间的空白栏中， 然后单击左下方的按键“Visualize Execution”。

### 在线调试环境2

- 单击右方的[Jupyter Notebook](https://mybinder.org/v2/gh/ipython/ipython-in-depth/master?filepath=binder/Index.ipynb)，稍后在浏览器里会显示Jupyter Notebook的运行环境。
- 在File的第一个下拉菜单“New Notebook” 的右侧箭头处选择“Python 3”，然后会显示一个新的页面
- 把下面的这段python代码拷贝到这个页面“In [ ]:”右侧的空白栏中， 然后单击上方的按键“运行”。

### 在线调试环境3

- 单击右方的[Python Online Compiler](https://trinket.io/python3/a5bd54189b)，稍后在浏览器里会显示python的运行环境。
- 把下面的这段python代码拷贝到这个页面左侧的空白栏中， 然后单击上方的按键“Run”。

```python
def identity_matrix(n):
    '''
    Creates an identity matrix of size n x n.

    INPUT
    * n - size of the Identity matrix

    OUPUT
    * identity matrix as a list of lists
    '''
    identity = []
    
    for r in range(n):
        new_row = []
        for c in range(n):
            if r == c: # Diagonals are only ones
                new_row.append(1)
            else: # Everything else is zero
                new_row.append(0)
        identity.append(new_row)
    
    return identity

# Run this cell to see if your answers are as expected

assert identity_matrix(1) == [[1]]

assert identity_matrix(2) == [[1, 0], 
                             [0, 1]]

assert identity_matrix(3) == [[1, 0, 0],
                             [0, 1, 0],
                             [0, 0, 1]]

assert identity_matrix(4) == [[1, 0, , 0],
                             [0, 1, 0, 0],
                             [0, 0, 1, 0],
                             [0, 0, 0, 1]]

# Copied over transpose, dot_product and matrix_multiplication
# created in previous exercises

def transpose(matrix):
    matrix_transpose = []
    for c in range(len(matrix[0])):
        new_row = []
        for r in range(len(matrix)):
            new_row.append(matrix[r][c])
        matrix_transpose.append(new_row)
    
    return matrix_transpose

def dot_product(vectorA, vectorB):
    result = 0
    
    for i in range(len(vectorA)):
        result += vectorA[i] * vectorB[i]
        
    return result

def matrix_multiplication(matrixA, matrixB):
    product = []

    transposeB = transpose(matrixB)

    for r1 in range(len(matrixA)):
        new_row = []
        for r2 in range(len(transposeB)):
            dp = dot_product(matrixA[r1], transposeB[r2])
            new_row.append(dp)
        product.append(new_row)

    return product

# Run this cell to see if your results are as expected.

m = [[5, 9, 2, 4],
     [3, 8, 5, 6],
     [1, 0, 0, 15]]

assert matrix_multiplication(m, identity_matrix(4)) == m
assert matrix_multiplication(identity_matrix(3), m) == m
```

## 参考文献及资料

1. [Coding Identity Matrix (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/01be5486-653f-4f50-90a9-ca9ef45bd6c0)
