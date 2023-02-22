---
layout: post
title: canonical & correspondence analysis
date: 2023-02-16 11:12:00-0400
description: CCA
tags: LinearAlgebra DataScience
categories: 
---

## Block Matrices

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/matrix blocks.png" title="An example of comparison between multiple regresion and pathway analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

$$
Y_{11}=
\begin{bmatrix}
    y_{11} & y_{12} \\
    y_{21} & y_{22} \\
    y_{31} & y_{32}
\end{bmatrix}
,
Y_{12} =
\begin{bmatrix}
    y_{13} & y_{14} \\
    y_{23} & y_{24} \\
    y_{33} & y_{34}
\end{bmatrix},
Y_{21} =
\begin{bmatrix}
    y_{41} & y_{42} \\
    y_{51} & y_{52} 
\end{bmatrix},
Y_{22} =
\begin{bmatrix}
    y_{43} & y_{44} \\
    y_{53} & y_{54} 
\end{bmatrix},
$$

where: $$\mathbb{Y_{11}, Y_{12}, Y_{21}, Y_{22}}$$ are called blocks of **Y**, while **Y** is called a block matrix consisting of $$\mathbb{Y_{11}, Y_{12}, Y_{21}, Y_{22}}$$.

Here, a block matrix of data is arranged horizontally:

$$
\mathbb{X}=\begin{bmatrix}
    \mathbb{X_1, \cdots, X_j, \cdots, X_J}
\end{bmatrix}
$$

and a block matrix of parameters is arranged vertically:

$$
\mathbb{C}=\begin{bmatrix}
    \mathbb{C_1} \\
    \vdots \\
    \mathbb{C_j} \\
    \vdots \\
    \mathbb{C_J}
\end{bmatrix}
$$

where $$\mathbb{X_j, C_j}$$ are called the jth block of **X** and **C**, respectively.

$$
\mathbb{XC}=\sum_{j=1}^{J}\mathbb{X_jC_j}=\mathbb{X_1C_1}+ \cdots + \mathbb{X_JC_J}
$$

## Canonical Correlation Analysis
Let's consider an n-individuals-p-variables data matrix $$\mathbb{X=[X_1, X_2]}$$ consisting of two blocks $$\mathbb{X_1}=[\vec{x_{11}}, \cdots, \vec{x_{1p_1}}](n \times p_1)$$ and $$\mathbb{X_2}=[\vec{x_{21}}, \cdots, \vec{x_{2p_2}}](n \times p_1)$$. That is, the p variables in **X** are classified into a group of $$p_1, p_2$$ variables. 

Canonical correlation analysis (CCA) with two blocks is formulated as minimizing

$$
\tag{1}
\begin{equation}
    f(\mathbb{C_1, C_2})=\lVert \mathbb{X_1C_1-X_2C_2} \rVert^2
\end{equation}
$$

subject to 

$$
\frac{1}{n}\mathbb{C_1^TX_1^TX_1C_1}=\frac{1}{n}\mathbb{C_2^TX_2^TX_2C_2}=\mathbb{I_m}
$$

That is, the purpose of CCA is to obtain the coefficient matrices **C1** and **C2** that allow **X1C1** and **X2C2** to be mutually best matched.

