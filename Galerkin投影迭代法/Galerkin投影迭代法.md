# Galerkin投影迭代法

$\lambda f(x) - \int_a^{b} k(x,y)f(y) dy = g(x)$

# 可修改参数

* 方程参数
  
  * Lambda: 对应方程$\lambda$
  
  * begin: 对应方程中的 a，修改为任意数字
  
  * end: 对应方程中的 b，修改为任意数字
  
  * K(x,y): 对应方程中的K(x,y)，修改为**sympy**函数，我这里事先已经定义了sympy变量x,y，并且声明sympy为sp，因此可以如下进行调整，来修改核函数。
    * ```python
      K = sp.exp(x*y)  
      ```
    * ```python
      K = sp.sin(x**2*y)
      ```
  
  * f_origin: 先给出你希望的$f(x)$的样子，程序会自动计算得出$g(x)$。注意只能使用$x$，不能使用$y$作为变量。具体修改方法见修改$K(x,y)$。
  
  * method: 采用不同的基函数，可以选择帽子函数：method = 'linear' 或者三角函数： method='trigo'
  
* 作图参数
  * start: 由于后续采用不同个数基函数来进行比较作图，start为最少的基函数个数。
  * total: 总共作图数
  * span: 跨度，作图选取的基函数个数的增加步长
  * y_tol: 由于采用迭代法，可能会造成部分基函数个数下出现端点爆炸的情况，因此将图片限制y的大小。y_tol为基于f_origin允许绘图的y的区间。比如y_origin在所求区间内最大为5，最小为1；如果设置y_tol = 5，则会作图 $y\in (5-1,5+5)$区间的曲线。

# 运行方法

1. 在电脑上安装Jupyter notebook的环境。（基本上只需要安装python环境，打开vscode或者pycharm等IDE，它会自动帮你安装完毕）
2. 安装程序依赖:

   ```shell
   $ pip install sympy
   $ pip install numpy
   $ pip install matplotlib
   ```
3. 打开文件，可以逐个代码块运行，也可以直接全部运行
4. 最终得到两张图片，上面一张是直观曲线图，下一张的logy的误差图。
