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

$ \dot{x}  = Ax+Bu $

$ y  =  Cx+Du $

其中$x(t_0) = x_0 $为状态变量，$ u $表示系统输入， $y$表示系统输出。

对应经典控制理论，两边取Laplace变换:

$ sX(s) = A X(s) + B U(s)$

$ Y(s) = C X(s) + D U(s)$

传递函数 $ G(s) = \frac{Y(s)}{U(s)} = (C(sI-A)^{-1}+D)$


### 五类系统性分析

#### 稳定性 Stability

对于传递函数$G(s)=C(sI-A)^{-1}+D$，$(sI-A)^{-1} = \frac{(sI-A)^{* }}{|sI-A|} $，其分母对应转移矩阵$A$的特征值，即传递函数极点。
对0输入系统，其稳定性判据为：**A的特征值的实部都在复平面左半平面**，对应极点对稳定性的影响。

#### 可控性 Controllability

可控性判据：**可控性矩阵$Co = [B\quad AB\quad A^{2}B\quad ……\quad A^{n-1}B]$满秩。** 由n阶系统的线性迭代形式推导，$  x_n = [B\quad AB\quad A^{2}B\quad … \quad A^{n-1}B] [ u_0\quad u_1\quad u_2 \quad… \quad u_{n-1}]^T $。即若使输入$u$有唯一解则转移矩阵必满秩。

``` 
rank(ctro(A, B))
```

#### 可稳定性 Stabilizability

存在状态负反馈使得系统稳定，判据：**任意实部大于0的A的特征值$\lambda$，矩阵$[A-\lambda I,\;B]$行满秩。**

#### 可观性 Observability

由于实际状态量可能不可测量，引入系统可观性，其判据为**是否可以通过系统输入和输出来得到系统的状态。** 

O={ [  C\\ CA\\ CA^{2}\\ ·\\ ·\\ CA^{n-1}]}


#### 可检测性：Detectablility





You can use the [editor on GitHub](https://github.com/jiaoly/jiao.github.io/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.
This sentence uses delimiters to show math inline: $\sqrt{3x-1}+(1+x)^2$

$$\sqrt{3x-1}+(1+x)^2$$


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
