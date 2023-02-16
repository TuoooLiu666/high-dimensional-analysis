## Prediction of a Dependent Variable by Explanatory Variables
we treat regression analysis, whose purpose is to predict or explain a variable from a set of other variables.

$$
\tag{1}
\vec{y}=\mathbb{X}\vec{b}+c\vec{1_n}+\vec{\epsilon}
$$


## Least Squares Method
Parameters b and c can be estimated using a least squares method. It generally refers to a class of the procedures for obtaining parameter values that minimize the sum of squared errors. 

$$
\tag{2}
||\vec{\epsilon}||^2=\sum_{i=1}^{n}\epsilon_i^2=||\vec{y}-\mathbb{X}\vec{b}+c\vec{1_n}||^2
$$

Thus, regression analysis is formulated as

minimizing $f(\vec{b}, c)= ||\vec{y}-\mathbb{X}\vec{b}-c\vec{1_n}||^2$ over $\vec{b}$ and c.

$$
\tag{3}
\vec{\epsilon}=\vec{y}-\mathbb{X}\vec{b}-c\vec{1_n}=\mathbb{J}\vec{y}-\mathbb{JX}\vec{b}
$$
where:
- $\mathbb{J}=\mathbb{I_n}-n^{-1}\vec{1_n}\vec{1_n}^T$ is the centering matrix
  
So (2) can be rewritten as
$$
||\vec{\epsilon}||^2=||\mathbb{J}\vec{y}-\mathbb{JX}\vec{b}||^2
$$

This is minimized when $\vec{b}$ is

$$
\vec{\hat{b}}=(\mathbb{X^TJX})^{-1}\mathbb{X^TJ}\vec{y}
$$
where:
- $(\mathbb{X^TJX})^{-1}$ is the inverse of $\mathbb{X^TJX}$ only if its non-singular.


## Predicted and Error Values
The predicted value vector is defined as
$$
\hat{\vec{y}}=\mathbb{X}\hat{\vec{b}}+\hat{c}\vec{1_n}
$$

## Proportion of Explained Variance and Multiple Correlation
To introduce a statistic that indicates how successful the results of regression analysis are using three properties of $\hat{\vec{y}}$ and $\hat{\vec{\epsilon}}$.

$$ 
\mathbb{J}\hat{\vec{y}}=\mathbb{JX}\hat{\vec{b}} 
$$

the average of an error vector is always zero:
$$
\mathbb{J}\hat{\vec{\epsilon}}=\hat{\vec{\epsilon}}
$$

errors are uncorrelated to predicted values:
$$
\hat{\vec{\epsilon}}^T\mathbb{J}\hat{\vec{y}}=0
$$

The proportion ofexplained variance is defined as
$$
\tag{4}
\frac{||\mathbb{J}\hat{\vec{y}}||^2}{||\mathbb{J}\vec{y}||^2}=1-\frac{||\hat{\vec{\epsilon}}||^2}{||\mathbb{J}\vec{y}||^2}
$$