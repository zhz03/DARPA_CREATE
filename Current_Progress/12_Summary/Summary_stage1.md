# Summary

## 1 Easy Problem

### Problem statement: - Single time step binary hypothesis 

- Given A,B,H,Q,R of a sensor. We will use this particular sensor to observe physical quantities for a long period of time (ex: t=100). Assuming on the next time step: t+1, given u_t=1 or 0,

- Compute the probability that decide u_t=1 given the fact that u_t=1 ? the probability that decide u_t=0 given the fact that u_t=1 ? the probability that decide u_t=1 given the fact that u_t=0 ? the probability that decide u_t=0 given the fact that u_t=0 ?

### Problem clarification

The problem we are trying to answer is actually a hypotheses  testing in a binary situation.  Assuming that we have two hypotheses: 

- $H_0:u_t = 0$ (no events happen case)
- $H_1: u_t = 1$ (events happen case)

There are four possibilities:

- $H_1$ is true, decide $H_1$ : given the $H_1$ is true hypothesis, decide H1 is in force: 

  $Prob\{decide H_1 |H_1 true\} =P_D$ (probability of detection)

- $H_0$ is true, decide $H_1$ : given the H0 is true hypothesis, decide $H_1$ is in force: 

  $Prob\{decide H_1 |H_0 true\} =P_{FA}$ (probability of false alarm)

- $H_1$ is true, decide $H_0$ : 

  $Prob\{decide H_0│H_1 true\}=P_M=1-P_D$ (probability of missing)

-  $H_0$ is true, decide $H_0$: 

  $Prob\{decide H_0│H_0 true\}=P_{CR}=1-P_{FA}$ (probability of correct rejection)

### Problem solution

- Consider system model and observation model:

  - prior: $x_t |z_{0:t},u_{0:t-1} \sim N(μ_{t|t},\Sigma_{t|t})$

  - system model: $x_{t+1}=Ax_t+Bu_t+w_t,w_t \sim N(0,Q)$

    where $x_{t+1}|x_t \sim N(Ax_t+Bu_t,Q)$

  - observation model: $z_{t+1}=Hx_{t+1}+v_t,v_t \sim N(0,R)$

    where $z_t|x_t \sim N(Hx_t,R)$

- Derivation:

  If using Kalman filter as linear quadratic optimal estimator, the Kalman prediction step to estimate state $x$ and its likelihood: 

  - $\mu_{t+1|t} = A\mu_{t|t} + Bu_t$

  - $\Sigma_{t+1|t}=A\Sigma_{t|t}A^T + Q$

  The update step:

  - $\mu_{t+1|t+1} = \mu_{t+1|t} + K_{t+1|t}(z_{t+1}-H\mu_{t+1|t})$

  - $\Sigma_{t+1|t+1}=(I-K_{t+1|t}H)\Sigma_{t+1|t}$

  Kalman Gain: 

  - $K_{t+1|t} = \Sigma_{t+1|t}H^T(H\Sigma_{t+1|t}H^T+R)^{-1}$

  In the Kalman filter, the objective is to calculate: $p_{t+1|t+1}(x)$
  $$
  p_{t+1|t+1}(x) = \frac{p(z_{t+1}|x)p_{t+1|t}(x)}{p(z_{t+1}|z_{0:t},u_{0:t})}
  $$
  In our case, the objective is to calculate uncertainty of the input in the last time step $u_t$. More specifically, given a binary candidate input sequences $u_{t}^j = \{0,1\},j\in \{1,2\}$, evaluate the likelihood of each input over time given only observations $z_{0:t+1}$

  Therefore, the error probability function that this problem is trying to compute is: $pdf(u_t|z_{0:t+1},x_{0:t},u_{0:t-1})$, denote it as $pdf(U)$
  $$
  pdf(u_t|z_{0:t+1},x_{0:t},u_{0:t-1}) = pdf(U) = z_{t+1} - HA\mu_{t|t} = z_{t+1} - H\mu_{t+1|t}
  $$
  In the Kalman filter, $pdf(U)$ is also Gaussian under each hypothesis and its distribution is as follows:
  $$
  U(z+1) \sim \left\{
  \begin{aligned}
  N(\mu_{u^1},\Sigma_{u^1}) & & under H_0\\
  N(\mu_{u^2},\Sigma_{u^2}) & & under H_1
  \end{aligned}
  \right.
  $$
  $\mu_{u_t} = \mathbf{E}[z_{t+1} - H\mu_{t+1|t}] = \mathbf{E}[Hx_{t+1}+v_t - H\mu_{t+1|t}] = \mathbf{E}[HA\mu_{t|t}+v_t - H(A\mu_{t|t} + Bu_t)] = \mathbf{E}[v_t + HBu_t] = HB\mathbf{E}[u_t]$

  $\Sigma_{u_t}=\mathbf{Var}[z_{t+1} - H\mu_{t+1|t}]\overset{indepen}{=}\mathbf{Var}[z_{t+1}] = \mathbf{Var}[Hx_{t+1}+v_t ] = H\Sigma_{t+1|t}H^{-1} + R = H(A\Sigma_{t|t}A^T + Q)H^{-1} + R$ 

