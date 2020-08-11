# End-End 1d implementation

## Code structure

### 1 E2E_stats_error_prob function

- This function takes $A,B,H,Q,R,x_0,uts,ts,sam_{numb}$ as inputs.

Where,

 $A,B,H,Q,R$ are system matrices,

$x_0$ is initial state

$uts$ is system inputs

$ts$ is time duration for inputs

$sam_{numb}$ is the sample numbers = 1000

- This function outputs statistical error probabilities: $Prob_D^{stats},Prob_{FA}^{stats},Prob_M^{stats},Prob_{CR}^{stats}$ 

### 2 E2E_error_prob function

- This function takes $A,B,H,Q,R,x_0,uts,ts$ as inputs.
- This function outputs theoretical error probabilities:  $Prob_D,Prob_{FA},Prob_M,Prob_{CR}$ 

### 3 E2E_comp function

- This function  takes $A,B,H,Q,R,x_0,uts,ts,sam_{numb}$ as inputs.

- Compare the difference between statistical error probabilities and theoretical error probabilities in order to verify this End-to-End pipeline: 

$$
error_{D,FA,M,CR} = Prob_{D,FA,M,CR}^{stats} - Prob_{D,FA,M,CR}
$$

## Comparison test

This comparison test is to show that with different $A,B,H,Q,R$, how big is the $error_{D,FA,M,CR}$

### Case 1: different Q

$$
Q = [0.1^2\sim 1^2]
$$

| Error mean   | value   |
| ------------ | ------- |
| $error_D$    | 0.0005  |
| $error_{FA}$ | 0.0005  |
| $error_{M}$  | -0.0005 |
| $error_{CR}$ | -0.0005 |

### Case 2: different R

$$
R = [0.1^2\sim 2^2]
$$

| Error mean   | value   |
| ------------ | ------- |
| $error_D$    | 0.0054  |
| $error_{FA}$ | 0.0008  |
| $error_{M}$  | -0.0054 |
| $error_{CR}$ | -0.0008 |

### Case 3: different A

$$
A = [0.5\sim 1.5]
$$

| Error mean   | value   |
| ------------ | ------- |
| $error_D$    | -0.0009 |
| $error_{FA}$ | -0.0018 |
| $error_{M}$  | 0.0009  |
| $error_{CR}$ | 0.0018  |

### Case 4: different H

$$
H = [0.5\sim 1.5]
$$

| Error mean   | value   |
| ------------ | ------- |
| $error_D$    | 0.0007  |
| $error_{FA}$ | -0.0005 |
| $error_{M}$  | -0.0007 |
| $error_{CR}$ | 0.0005  |

### Conclusion

From the error comparison, we found that almost all mean errors are less then 0.5%. We can say that in the parameters space we tested, the end-to-end validation is accurate.   