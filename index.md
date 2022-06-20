<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

### 研究对象和方法

有限维线性时不变动态系统（a finite dimensional linear time invariant (FDLTI) dynamical system），具有齐次性、线性和时不变特性

使用线型常微分方程组描述系统

$$ \begin{array}{c}
\dot{x}  = Ax+Bu \\
 y  =  Cx+Du 
 \end{array}$$

其中$x(t_0) = x_0 $为状态变量，$ u $表示系统输入， $y$表示系统输出。

对应经典控制理论，两边取Laplace变换:

$$ \begin{array}{c}
sX(s) = A X(s) + B U(s)\\
Y(s) = C X(s) + D U(s)
\end{array}$$

传递函数 $ G(s) = \frac{Y(s)}{U(s)} = (C(sI-A)^{-1}+D)$


### 五类系统性分析

#### 稳定性 Stability

对于传递函数$G(s)=C(sI-A)^{-1}+D$，$(sI-A)^{-1} = \frac{(sI-A)^{* }}{|sI-A|} $，其分母对应转移矩阵$A$的特征值，即传递函数极点。
对0输入系统，其稳定性判据为：**A的特征值的实部都在复平面左半平面**，对应极点对稳定性的影响。

#### 可控性 Controllability

可控性判据：**可控性矩阵$Co = [B\quad AB\quad A^{2}B\quad ……\quad A^{n-1}B]$行满秩。** 由n阶系统的线性迭代形式推导如下
[B\quad AB\quad A^{2}B\quad … \quad A^{n-1}B] 

$$ x_n = [B\quad AB\quad A^{2}B\quad … \quad A^{n-1}B] 
\begin{bmatrix} 
u_0 \\ 
u_1 \\ 
u_2 \\ 
... \\ 
u_{n-1} 
\end{bmatrix} $$

即若使输入$u$有唯一解则转移矩阵必满秩。

``` 
rank(ctro(A, B))
```

#### 可稳定性 Stabilizability

存在状态负反馈使得系统稳定，判据：**任意实部大于0的A的特征值$\lambda$，矩阵$[A-\lambda I, B]$行满秩。**

#### 可观性 Observability

由于实际状态量可能不可测量，引入系统可观性，即是否可以通过系统输入和输出来得到系统的状态。

其判据为**可观测矩阵$O$列满秩**，其中

$$O = \begin{bmatrix}
 C\\
 CA\\
CA^2 \\
: \\
CA^{n-1}
\end{bmatrix}$$

Matlab判断语句为
```
rank(obsv(A, C))
```

#### 可检测性：Detectablility

根据可控性和可观性是对偶的，同理，可检测性是可稳定性的对偶概念，含义是：观测器系统是不是可稳定的。判据是：**任意实部大于0的A的特征值$\lambda$ ，矩阵**

$$ \begin{bmatrix} \lambda I -A \\ 
B \end{bmatrix}$$

**列满秩。**

### 状态反馈稳定控制

基于状态方程的系统如下，其系统输入u与状态变量$x$无关，因此不构成反馈。其状态方程

$$\begin{array}{c}
\dot{x}  = Ax+Bu \\
 y  =  Cx+Du 
\end{array}$$

![img](/Figures/feedback_fig.png)

基于状态反馈的控制系统如下:

![img](/Figures/state_feedback_fig.png)

其中$ U = Fx$，即输入为状态变量的函数，通过状态反馈实现稳定控制。确定这一线性变换F的过程也是配置极点的过程，Matlab实现如下

'''
F = -place(A, B, eig_value)
'''

在以上系统中通过输入u实现对系统的稳定控制，也即对状态变量误差的控制。对于Tracking问题则需对误差$e = {x_d} - x$进行反馈控制，其中$x_d$为期望值。为将开环平衡点放置在0点，将e替换对应状态变量。其系统如下：



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List
- 
This sentence uses $ delimiters to show math inline: $\sqrt{3x-1}+(1+x)^2$


1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/jiaoly/jiao.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
