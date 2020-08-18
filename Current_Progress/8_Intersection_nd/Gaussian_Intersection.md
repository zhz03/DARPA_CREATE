# Gaussian Intersection

The multivariate Gaussian distribution of a k-dimension random variable $X = [X_1,X_2,...,X_k]^T$ can be written in the following notation:
$$
\mathbf{X} \sim N(\mathbf{\mu},\mathbf{\Sigma})
$$

## n-d Density function

$$
f_{\mathbf{x}}(x_1,...,x_k) = \frac{1}{\sqrt{(2\pi)^k|\Sigma|}}exp^{(-\frac{1}{2}(\mathbf{x}-\mathbf{\mu})^T\mathbf{\Sigma}^{-1}(\mathbf{x}-\mathbf{\mu}))}
$$

where,

$\mathbf{x}$ is a read k-dimensional column vector,

$|\Sigma| = det(\Sigma)$ is the determinant of $\Sigma$

## Solve for intersection of two n-d Gaussian distribution

To solve for the intersection of two n-d Gaussian distribution, mathematically, we actually need to solve for $\mathbf{x}$ when $f1_{\mathbf{x}}(x_1,...,x_k)=f2_{\mathbf{x}}(x_1,...,x_k)$

### Solution:

Let $f_1(x) = f1_{\mathbf{x}}(x_1,...,x_k)$ , $f_2(x) = f2_{\mathbf{x}}(x_1,...,x_k)$ and take the log of both sides

$\Rightarrow log(f_1(x)) = log(f_2(x))$

$\Rightarrow log(f_1(x)) - log(f_2(x)) = 0$

Assume $f_i(x)$ has known mean $\mathbf{\mu_i}$ and covariance $\mathbf{\Sigma_i}$ then: 

$log(f_i(x)) = -\frac{k}{2}log(2\pi)-\frac{1}{2}log(|\mathbf{\Sigma}_i|)-\frac{1}{2}((\mathbf{x}-\mathbf{\mu_i})^T\mathbf{\Sigma_i}^{-1}(\mathbf{x}-\mathbf{\mu_i}))$

Therefore:

$ log(f_1(x)) - log(f_2(x))$

$ = \frac{1}{2}[log(|\mathbf{\Sigma}_2|)-log(|\mathbf{\Sigma}_1|)+(\mathbf{x}-\mathbf{\mu_2})^T\mathbf{\Sigma_2}^{-1}(\mathbf{x}-\mathbf{\mu_2})-(\mathbf{x}-\mathbf{\mu_1})^T\mathbf{\Sigma_1}^{-1}(\mathbf{x}-\mathbf{\mu_1})] $

$= 0$

### 2-d Scenario 

$ \mathbf{x} = [x_1,x_2]^T, \Sigma_1=\begin{bmatrix}
\Sigma_1^{11} & \Sigma_1^{12} \\
\Sigma_1^{21} & \Sigma_1^{22} 
\end{bmatrix}, \Sigma_2= \begin{bmatrix}
\Sigma_2^{11} & \Sigma_2^{12} \\
\Sigma_2^{21} & \Sigma_2^{22} 
\end{bmatrix} , \mathbf{\mu_1} = [\mu_1^{x_1},\mu_1^{x_2}]^T, \mathbf{\mu_2} = [\mu_2^{x_1},\mu_2^{x_2}]^T $

$ log(f_1(x)) - log(f_2(x)) = 0$

$= log(|\mathbf{\Sigma}_2|)-log(|\mathbf{\Sigma}_1|)+(\mathbf{x}-\mathbf{\mu_2})^T\mathbf{\Sigma_2}^{-1}(\mathbf{x}-\mathbf{\mu_2})-(\mathbf{x}-\mathbf{\mu_1})^T\mathbf{\Sigma_1}^{-1}(\mathbf{x}-\mathbf{\mu_1}) = 0$

$= log(\frac{\Sigma_2^{11}\Sigma_2^{22}-\Sigma_2^{12}\Sigma_2^{21}}{\Sigma_1^{11}\Sigma_1^{22}-\Sigma_1^{12}\Sigma_1^{21}}) + \frac{1}{\Sigma_2^{11}\Sigma_2^{22}-\Sigma_2^{12}\Sigma_2^{21}}[x_1-\mu_2^{x_1},x_2-\mu_2^{x_2}]\begin{bmatrix} \Sigma_2^{11} & -\Sigma_2^{12} \\ -\Sigma_2^{21} & \Sigma_2^{22}  \end{bmatrix} \begin{bmatrix} x_1-\mu_2^{x_1} \\ x_2-\mu_2^{x_2}  \end{bmatrix} - $

$\frac{1}{\Sigma_1^{11}\Sigma_1^{22}-\Sigma_1^{12}\Sigma_1^{21}}[x_1-\mu_1^{x_1},x_2-\mu_1^{x_2}]\begin{bmatrix} \Sigma_1^{11} & -\Sigma_1^{12} \\ -\Sigma_1^{21} & \Sigma_1^{22}  \end{bmatrix} \begin{bmatrix} x_1-\mu_1^{x_1} \\ x_2-\mu_1^{x_2}  \end{bmatrix}$

**Special case:**

$ \mathbf{x} = [x_1,x_2]^T, \Sigma_1=\Sigma_2= \begin{bmatrix}
\sigma_{11}^2 & 0 \\
0 & \sigma_{22}^2 
\end{bmatrix} , \mathbf{\mu_1} = [0,0]^T, \mathbf{\mu_2} = [1,1]^T $

$ log(f_1(x)) - log(f_2(x)) = 0$

$\Rightarrow 1-2x = -1 + 2y$

$\Rightarrow 1-x = y$

