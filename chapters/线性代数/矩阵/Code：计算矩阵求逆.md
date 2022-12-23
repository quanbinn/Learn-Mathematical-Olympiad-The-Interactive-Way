# Code：计算矩阵求逆

## 开始做代码实验

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
def inverse_matrix(matrix):
    '''
    Return the inverse of 1x1 or 2x2 matrices.
    
    Raises errors if the matrix is not square, is larger
    than a 2x2 matrix, or if it cannot be inverted due to
    what would be a division by zero.
    '''
    
    inverse = []
    
    # Check if not square
    if len(matrix) != len(matrix[0]):
        raise ValueError('The matrix must be square')
    
    # Check if matrix is larger than 2x2.
    if len(matrix) > 2:
        raise NotImplementedError('this functionality is not implemented')
    
    # Check if matrix is 1x1 or 2x2.
    # Depending on the matrix size, the formula for calculating
    # the inverse is different. 
    if len(matrix) == 1:
        inverse.append([1 / matrix[0][0]])
    elif len(matrix) == 2:
        # If the matrix is 2x2, check that the matrix is invertible
        if matrix[0][0] * matrix[1][1] == matrix[0][1] * matrix[1][0]:
            raise ValueError('The matrix is not invertible.')
        else:
            # Calculate the inverse of the square 1x1 or 2x2 matrix.
            a = matrix[0][0]
            b = matrix[0][1]
            c = matrix[1][0]
            d = matrix[1][1]
            
            factor = 1 / (a * d - b * c)
            
            inverse = [[d, -b],[-c, a]]
            
            for i in range(len(inverse)):
                for j in range(len(inverse[0])):
                    inverse[i][j] = factor * inverse[i][j]
    
    return inverse

# Run this cell to check your output. If this cell does 
# not output anything your answers were as expected.

assert inverse_matrix([[100]]) == [[0.01]]
assert inverse_matrix([[4, 5], [7, 1]]) == [[-0.03225806451612903, 0.16129032258064516],
 [0.22580645161290322, -0.12903225806451613]]

# Run this line of code and see what happens. Because ad = bc, this
# matrix does not have an inverse
inverse_matrix([[4, 2], [14, 7]])

# Run this line of code and see what happens. This is a 3x3 matrix
inverse_matrix([[4, 5, 1], [2, 9, 7], [6, 3, 9]])
```

## 参考文献及资料

1. [Coding Matrix Inverse (Solution)](https://classroom.udacity.com/courses/ud953/lessons/4632564251/concepts/c0816e85-55c5-4356-8d65-6046a2837d51)