# Binary hypothesis testing nd

## N-dimension binary hypothesis testing equations 

$$
u_t=\left\{
\begin{aligned}
H_0: 0 & (ðð ðð£ððð¡ð  âððððð ððð ð)  \\
H_1: 1 & (ðð£ððð¡ð  âððððð ððð ð) \\
\end{aligned}
\right.
$$

* $Prob\{decide H_1 |H_1 true\} =P_D = â« \limits_{D} N(HBâ1,Ï^2)$ // latex words in Latex 

* $Prob\{decide H_1 |H_0 true\} =P_{FA} = \int \limits_{D} N(HBâ0,Ï^2)$

* $Prob\{decide H_0âH_1 true\}=P_M=1-P_D$

* $Prob\{decide H_0âH_0 true\}=P_{CR}=1-P_{FA}$

  where, $D = \{f(HBâ1,Ï^2) > f(HBâ0,Ï^2)\}$

Based on these equations, for high-dimensional cases, we used sampling based algorithm to calculate the intersection and $P_D,P_{FA},P_M,P_{CR}$

Take 2d cases as example. In the following pictures, The red region is where $abs(f(HBâ1,Ï^2) - f(HBâ0,Ï^2))<0.001$

## Case study

### Scenario 1:

$\Sigma_1 = \Sigma_0$  case

#### Example 1

$$
\Sigma_0=\Sigma_1= \begin{bmatrix}
0.2 & 0 \\
0 & 0.2 
\end{bmatrix}
$$

$P_D = 0.9421,P_{FA}=0.0561,P_M=0.0579,P_{CR}=0.9438$

![Figure_1](figs/Figure_1.png)



#### Example 2

$$
\Sigma_0= \Sigma_1= \begin{bmatrix}
0.4 & -0.2 \\
-0.2 & 0.4 
\end{bmatrix},
$$

$P_D = 0.9421,P_{FA}=0.0561,P_M=0.0579,P_{CR}=0.9438$

![Figure_1](figs/Figure_2.png)

#### Example 3

$$
\Sigma_0= \Sigma_1= \begin{bmatrix}
0.4 & 0.2 \\
0.2 & 0.4 
\end{bmatrix},
$$

$P_D = 0.8203,P_{FA}=0.1821,P_M=0.1797,P_{CR}=0.8178$

![Figure_1](figs/Figure_3.png)

### Scenario 2

$\Sigma_1 \neq \Sigma_0$ with diagonal terms case

#### Example 1

$$
\Sigma_0= \begin{bmatrix}
0.3 & 0.1 \\
0.1 & 0.3 
\end{bmatrix},
\Sigma_0= \begin{bmatrix}
0.5 & 0.1 \\
0.1 & 0.5 
\end{bmatrix}
$$
$P_D = 0.8271,P_{FA}= 0.1268,P_M= 0.1729,P_{CR}= 0.8732$

![Figure_1](figs/Figure_4.png)

#### Example 2

$$
\Sigma_0= \begin{bmatrix}
0.3 & -0.1 \\
-0.1 & 0.3 
\end{bmatrix},
\Sigma_0= \begin{bmatrix}
0.5 & -0.3 \\
-0.3 & 0.5 
\end{bmatrix}
$$

$P_D = 0.9447,P_{FA}= 0.0548,P_M=0.0552,P_{CR}=0.9452$

![Figure_1](figs/Figure_5.png)

#### Example 3

$$
\Sigma_0= \begin{bmatrix}0.6 & 0.2 \\0.2 & 0.6 \end{bmatrix},\Sigma_0= \begin{bmatrix}
0.4 & 0.3 \\0.3 & 0.4 \end{bmatrix}
$$

$P_D = 0.8433,P_{FA}=0.1943,P_M=0.1567,P_{CR}=0.8057$

![Figure_1](figs/Figure_6.png)

### Scenario 3

magnitude between $\Sigma_1$ and $\Sigma_0$ is huge

#### Example 1

$$
\Sigma_0= \begin{bmatrix}
1 & 0.0 \\
0.0 & 1 
\end{bmatrix},
\Sigma_0= \begin{bmatrix}
0.2 & 0 \\
0 & 0.2 
\end{bmatrix}
$$
$P_D = 0.9371,P_{FA}=0.1704,P_M=0.0629,P_{CR}=0.8296$

![Figure_1](figs/Figure_7.png)

#### Example 2

$$
\Sigma_0= \begin{bmatrix}
0.2 & 0.1 \\
0.1 & 0.2
\end{bmatrix},
\Sigma_0= \begin{bmatrix}
1 & 0.2 \\
0.2 & 1 
\end{bmatrix}
$$
$P_D = 0.8236,P_{FA}=0.690,P_M=0.1763,P_{CR}=0.9310$

![Figure_1](figs/Figure_8.png)


#### Example 3

$$
\Sigma_0= \begin{bmatrix}
2 & -0.4 \\
-0.4 & 2 
\end{bmatrix},
\Sigma_0= \begin{bmatrix}
0.2 & -0.1 \\
-0.1 & 0.2 
\end{bmatrix}
$$
$P_D = 0.9867,P_{FA}=0.1344,P_M=0.0433,P_{CR}= 0.8656$

![Figure_1](figs/Figure_9.png)

## Key challenges

#### calculate the 3 $\sigma$ boundary

Sampling based algorithm to calculate the error probabilities $P_{D,M,CR,FA}$ and intersection is computational expensive. So we need to know the 3 $\sigma$ rule boundary of two normal distribution to figure out the total boundary.

To be more specific, in the following picture, how to calculate the $x_{range}=-4.2 \sim 6.3$ and $y_{range} = -4.2 \sim 6.3$ ?

![Figure_1](figs/Figure_11.png)

**Solution:** 

Mahalanobis distance:

$d = \sqrt{(x-\mu)^T\Sigma^{-1}(x-\mu)}$

if $d=3.0$, it corresponds to the "3-sigma"



