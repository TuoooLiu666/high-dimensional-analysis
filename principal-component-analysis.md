## Reduction of Variables into Components

PCA is usually used for an n-individuals $\times$ p-variables centered data matrix $\mathbb{X}$. For such a data matrix X, PCA can be formulated with
$$
\tag{1}
\mathbb{X}=\mathbb{FA^T}+\mathbb{E}
$$
where
- F is an n-individuals $\times$ m-components matrix whose elements are called principal component (PC) scores
- A is a p-variables $\times$ m-components matrix whose
elements are called component loadings
- E contains errors
  
The $k$th columns of F and A are called the $k$th components. That is, X is assumed to be approximated by the product of unknown matrices F and transposed A, with the number of columns (components) in F and A being smaller than that of X.

To obtain the PC score matrix F and loading matrix A, a least square method is used:
$$
\tag{2}
f(\mathbb{F,A})=||\mathbb{E}||^2=||\mathbb{X-FA^T}||^2
$$

is minimized over F and A. The relationships of the PC scores to the original four variables are described in A.  Such a reduction is called **reduced rank approximation**.

## Singular Value Decomposition
PCA solutions are given through the singular value decomposition (SVD) here. 

Any $n \times p$ matrix X with $rank(X) = r$ can be decomposed as
$$
\mathbb{X}=\mathbb{K \Lambda L^T}
$$
Here, $\mathbb{K, L}$ satisfy $\mathbb{K^TK}=\mathbb{L^TL}=\mathbb{I_r}$ and 
$$
\Lambda=
\begin{bmatrix}
    \lambda_1 & & \\
    & \ddots & \\
    & & \lambda_r
\end{bmatrix}
$$ is  an $r\times r$ diagonal matrix whose diagonal elements are positive and arranged in decreasing order

### SVD and Least Squares Solution
SVD has the following important property, which is directly related to the PCA solution minimizing (2):

Let X be an $n \times p$ matrix, then
$$
f(\mathbb{FA^T})=||\mathbb{X-FA^T}||^2
$$ is minimized for
$$
\mathbb{FA^T}=\mathbb{K_m \Lambda_m L^T_m}
$$

After deciding the number of components (m), F and A can be determined by
$$
\mathbb{F}=\mathbb{K_m \Lambda^\alpha_m S}
$$
and
$$
\mathbb{A}=\mathbb{L_m\Lambda_m^{1-\alpha} S^{-1}}
$$
with a and S being **arbitrary** scalar and nonsingular matrices, respectively.

## Constraints for Components
$$
\frac{1}{n}\mathbb{F^TF}=\mathbb{I_m}
$$
PCs are orthogonal to each other and $\mathbb{A^TA}$ is a diagonal amtrix. Implications:

- PC scores are standardized with mean 0 and variance 1
- PCs are orthogonal to each other
-  A ($p \times m$) is the *covariance matrix* between p variables and m components,  or the *correlation matrix* when X is standardized.

## Percentage of Explained Variance
$$
||\mathbb{E}||^2=||\mathbb{K \Lambda L^T-K_m \Lambda_m L^T_m}||^2=tr(\Lambda^2) - tr(\Lambda^2_m)
$$

$$
\tag{3}
PEV_m=\frac{tr(\Lambda^2_m)}{tr(\Lambda^2)}=\frac{tr(\Lambda^2_m)}{||\mathbb{X}||^2}
$$

## Reformulate PCA with Different Constraints
Let X denote an n-individuals by p-variables centered data matrix.  In SVD solution to PCA, $\alpha$ and S are arbitrary scalar and nonsingular matrices, respectively, which show that **infinitely** many solutions exist.

To select a single solution among them, we consider the following constraints:
$$
\mathbb{F^TF} = \mathbb{W^TX^TXW}
$$
a diagonal matrix whose diagonal elements are arranged in descending order, and $\mathbb{W=A=L_m}, \mathbb{W^TW=I_m}$.
Rewrite the objective function:
To minimize
$$
f(\mathbb{W})=||\mathbb{X-XWW^T}||^2
$$ without $\mathbb{A}$.

To minimize
$$
\tag{4}
\Rightarrow f(\mathbb{W})=tr(\mathbb{X^TX})-tr(\mathbb{W^TX^TXW})
$$
is equal to maximize $tr(\mathbb{W^TX^TXW})$. 

Now we can also rewrite $g(\mathbb{W})=tr(\mathbb{W^TX^TXW}) $ as
$$
    g(\mathbb{W})=tr(\mathbb{W^TX^TXW}) =tr(\mathbb{W^TVW})
$$
where
$$
\tag{5}
\mathbb{V=n^{-1}X^TX}
$$ is the covariance matrix for centered $\mathbb{X}$, which can be solved by Eigendecomposition.

## Eigendecomposition of a Covariance Matrix
The singular value decomposition $\mathbb{X = K \Lambda L^T}$ leads to $\mathbb{X^TX}=\mathbb{L\Lambda^2 L^T}$. Use (5), we get
$$
n\mathbb{V}=\mathbb{L\Lambda^2 L^T}
$$

This equation can be rewritten as
$$
\tag{6}
\mathbb{V}=\mathbb{L\Delta L^T}
$$
Here,
$$
\Delta=\begin{bmatrix}
    \delta_1 & & \\
    & \ddots & \\
    & & \delta_r
\end{bmatrix}=
\frac{1}{n}\mathbb{\Lambda^2}
$$

with $r=rank(\mathbb{X}), \delta_1 \ge \cdots \ge \delta_r \ge 0$.

Decomposition (6) is referred as Eigendecomposition (EVD),
where
- $\delta_k$  is called the kth largest eigenvalue of $\mathbb{V}$
- the kth column of $\mathbb{L}$ is called the eigenvector of $\mathbb{V}$ corresponding to $\delta_k$.


