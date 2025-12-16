## Recap
### 1. Random variable and sample space
$X = lifetime of a machine (hours)$
$S = \\{x \vert 0 \leq x \leq \infty\\}$
So $X$ is a continous random variable on $[0, \infty]$

### 2. Distribution: from probabilty to survival modeling
- To define probabilities, we specify a **probability distribution** for X.
- A **canonical example** in survival analysis is the **Exponential distribution**, which models constant failure risk.
- **Assumption**: The machine has a constant hazard (failure rate) $\lambda > 0$

### 3. Probability density function (PDF)
If $X \sim Exponential(\lambda)$, then 
$$
f(n)=
\begin{cases}
n/2 & n=2,4,6,\ldots \\
3n+1 & n=1,3,5,\ldots
\end{cases}
$$