## Recap
### 1. Random variable and sample space
- $X = lifetime of a machine (hours)$
- $S = \\{x \vert 0 \leq x \leq \infty\\}$ non-negative and continuous
- So $X$ is a continous random variable on $[0, \infty]$

### 2. Distribution: from probabilty to survival modeling
- To define probabilities, we specify a **probability distribution** for X.
- A **canonical example** in survival analysis is the **Exponential distribution**, which models constant failure risk.
- **Assumption**: The machine has a **constant hazard (failure rate) $\lambda > 0$**

### 3. Probability density function (PDF)
If $X \sim Exponential(\lambda)$, then \

$$
f(n)=\begin{cases}\lambda e^{\lambda x} & x \lge 0 \\0 & x<0> \end{cases}
$$

### 4. Cumulative distribution function (CDF)
The CDF gives:
$$
F_X(x) = P(X \leq x)
$$
For the exponential distribution:
$$
F_X(x)=\begin{cases}1-e^(-\lambda x), & x\geq 0 \\ 0, & x<0  \end{cases}
$$

### 5. Srvival function (core concept)
In survival analysis, we focus on the survival function:
$$
S(x) = P(X > x)
$$

Using the CDF:
$$
S(x) = 1- F_X(x)
$$

For the exponential model:
$$
S(x) = e^{-\lambda x}
$$

### 6. Event: "The machine works for at least 20 hours"
Your event is:
$$
A = \\{x\vert x\geq 20\\}
$$

So the probability is:
$$
P(X \geq 20) = S(20)\\
P(X \geq 20) = e^{-20\lambda}
$$

Interpretation:
If \lambda=0.05:$
$$
P(X \geq 20) = e^{-1} \approx 0.3679
$$
So about 36.8% of machines survive beyond 20 hours.

### 7. Hazard function (why survival analysis is special)
The hazard function is defined as:

$$
h(x) = \lim_{\Delta\rightarrow 0}\frac{P(x \leq X < x + \Delta x \vert X \geq x)}{\Delta x}
$$

For exponential districution:
$$
h(x) = \lambda (constant)
$$

Meaning:
The failure risk does not depend on age - a key modeling assumption.

### 8. Relationship between hazard and survival (important formula)
$$
S(x) = exp(-\int\limits_{0}^{x} h(t) dt)
$$

For constant hazard $h(t) = \lambda$ :
$$
S(x) = e^{\lambda x}
$$

### 9. Memoryless property (pure probability result)
The exponential distribution satistifes:
$$
P(X > x+t \vert X>s) = P(X>t)
$$

Interpretation:
If the machine has survived 100 hours, its future lifetimem distribution is the same as a brand-new one.

## Practical example: churn rate
- churn rate: the percentage of customers or subscribers who stop using a company's product or service over a specific time (like monthly or yearly), indicating customer loss and impacting revenue.

### 1. Settings
#### Define the random variable
$$
X = time (in months) until a user chruns
$$
#### Sample space and event
$$
S = \\{x \vert 0 \leq x < \infty \\}
A = \\{x\vert x \geq 6\\} : Event "The user is still active after 6 months"
So we want: P(X \geq 6)
$$

#### Survival function
- survival function = retention curve
- Define the survival function: $S(t) = P(X > t)$
- In churn language : $S(t)=Retention rate at time t$
- So "retention=survival", "churn=failure"

#### Simple churn model: constant churn rate
- Assumptions:
    - Users churn at a constant rate $\lmabda$ per month
    - This corresponds to an exponential survival month
    - PDF $f(t) = \lambda e^{-\lambda t}$
    - Survival function $S(t) = e^{-\lambda t}$

#### Practical numbers
Suppose:
- Monthly churn rate $\approx 5%$
- Then $\lambda = 0.05$

Retention after 6 months:
- $P(X \geq 6)=S(6)=e^{-0.05 \times 6}$
- $S(6) \approx e^{-0.3} \approx 0.741$
- Interpretation: About 74.1% of users remain after 6 months.

Churn probability in a time window
- Churn by 6 month : $P(churn within 6 months) = P(X \leq 6) = 1-S(6)$

Hazard function = instantaneous churn rate
- For exponential model: $h(t) = \lambda = 0.05$
- Interpretation: If a user is active at month t, their instantaneous chrun risk is still 5% per month.


## Qeustions
Q 1. why do we use exponential distribution to model constant failure risk. 
A 1. Because exponential is the only continuous distribution whose conditional failure probability does not depend on age.
- This is not a modeling convenience — it is a mathematical consequence.

Q 2. In survival analysis, why do we use the term "constant hazard", where does this come out?
A 2. 
- define the hazard rate
    - hazard: Given the user/system survived up to time $t$, what is the chance it fails in the next $\Delta t$?
- express hazard using PDF and survival function
- plug in the exponential distribution
- interpretation of **constant hazard**

Q 3. Why survival anaylsis usese **hazard** instead of just PDF
- PDF answers "When does failure occur in absolute time?"
- Hazard answers "Given survival so far, how risky is the next moment?"
- In churn, reliability, medicin:
    - Decisions are conditional on survival
    - Rick changes over time.
    - Hence hazard is the natural object.

Q 3. I still don't get it. why do you use exponential distribution for random variable x which is the lifetime of a machine? cause the distribution shape goes down. does it mean that lifetime gets greater? also when applying to churn rate, does it mean that the probability that the user is gonna leave goes down? also, why is it memoryless? cause if you look at exponential distribution, the value depends on x value.
A 3. it’s mixing up three different objects that look similar but mean very different things.
- The core mistake (let’s name it)
    - You are currently interpreting the PDF curve as:
    - “Probability that lifetime is getting bigger / smaller”
    - That interpretation is wrong, and it’s the root of all confusion.
    - So first, we must separate concepts.

- What does the exponential distrbution actually describe?
    - we are NOT saying: “Lifetime tends to be small”, “Probability of surviving goes down”, “Machines get weaker over time”
    - Those interpretations are false.
    - What the PDF really means (very important): Density of failure time around x. “At what time do failures tend to occur?”.
- Why does the exponential PDF go down then??
    - Because early failures are more common in absolute time, not because risk decreases.
    - Many machines fail early, Fewer machines survive long enough to fail late
- The object that represents "risk" is NOT the PDF
    - This is the key
    - **Risk = Conditional Probability**
    - The real question is "Given that the machine is still alive at time $t$, how risky is the next moment?". This is **hazard**, not PDF.
- Hazard vs. PDF
    - PDF $f(t)$
        - unconditional : "How many failures happen around time t among all machines?"
    - Hazard $h(t) = \frac{f(t)}{S(t)}$
        - conditional : "Among machines that survived to time t, how risky is the next instant?"
- Exponential distribution has constant hazard
    - $f(t)=\lambda e^{-\lambda t}$, $S(t)=e^{-\lambda t}$, $h(t)=\frac{f(t)}{S(t)}=\lambda$
    - This is the whole reason exponential is used.
- Why the PDF decreasing does NOT mean risk decreases
    - Let's use a concrete example. Assume:
        - 1,000 machines at time 0, hazard $\lambda=0.1$
        - At time 0 : 1,000 machines alive, ~100 fail in next unit time
        - At time 10 : Only ~367 machines alive, ~37 fail in next unit time
    - So:
        - Number of failures decreases -> PDF goes down
        - Risk per surviving machine stays the same -> hazard is constant
        - PDF goes down because population shrinks, not because risk shrinks.
    - Exponential distribution does not say “things get safer over time.”
    - It says: “Things never get safer or riskier — only fewer remain.”

- Further steps : Why exponential is a baseline, not a belief
    - In practice:
        - Humans get less likely to churn → decreasing hazard
        - Machines wear out → increasing hazard
    - That’s why: Weibull, Cox model exist.
    - Exponential is used because:
        - It is the only mathematically consistent model of constant conditional risk
        - It is the null model of survival analysis

Q 4. but why do we have to assume the constant failure? It might be not constant. also, based on the memoryless property the chance of failure dose not depend on how long the system has already sruvive. but in real life, it might depends on the past survival time. isn't it?
A 4. 
## Why assume constant failure (Exponential model)?

### Short answer

- We **do not have to assume constant failure**
- We assume it only as a **baseline / null model**
- In real life, failure **does depend on past survival time**

This is precisely why survival analysis exists.

---

## 1. Why assume constant failure at all?

In probability and statistics, modeling usually starts with the  
**simplest model consistent with minimal assumptions**.

Examples:
- Coin toss → Bernoulli
- Constant event rate → Poisson
- Gaussian noise → Normal

In survival analysis, the minimal assumption is:

> “Given survival so far, the failure risk does not change.”

This assumption uniquely leads to the **exponential distribution**.

So the exponential model should be understood as a **null hypothesis**:

> What would lifetime look like if aging or duration had no effect?

It is **not a belief about reality**, but a reference point.

---

## 2. Mathematical privilege of the exponential distribution

The exponential distribution is the **only continuous distribution**
that satisfies the memoryless property:

$$
P(X > s+t \mid X > s) = P(X > t)
\quad \forall s,t \ge 0
$$

This property makes the model:
- analytically simple
- identifiable
- interpretable
- composable

Hence, exponential survival is mathematically privileged as a baseline.

---

## 3. Real life violates memorylessness

In practice, the memoryless assumption is often false.

- **Machines**: early defects and wear-out failures
- **Users**: onboarding churn and long-term loyalty
- **Humans**: mortality risk increases with age

All of these imply:

$$
h(t) \neq \text{constant}
$$

---

## 4. Why survival analysis uses the hazard function

Instead of assuming constant risk, survival analysis generalizes to:

$$
h(t) = \text{any nonnegative function of time}
$$

The hazard function models **how risk evolves with survival time**.

---

## 5. Weibull distribution: one-step generalization

The Weibull hazard function is:

$$
h(t) = \lambda k t^{k-1}
$$

Interpretation:
- $k < 1$ : decreasing risk (early churn)
- $k = 1$ : constant risk (exponential)
- $k > 1$ : increasing risk (aging / fatigue)

The exponential distribution is the special case $k = 1$.

---

## 6. Why not always use more complex models?

More complex models require:
- more data
- stronger assumptions
- more parameters

Constant-hazard models are useful when:
- data is sparse
- time horizon is short
- interpretability matters
- a baseline comparison is needed

This tradeoff mirrors linear models vs deep learning.

---

## 7. Memorylessness is not a claim about reality

The memoryless assumption does **not** say the world has no memory.  
It says:

> “We do not encode age dependence unless data forces us to.”

It is an assumption about **conditional independence**, not belief.

---

## 8. Typical survival analysis workflow

1. Start with exponential (constant hazard)
2. Examine empirical survival or hazard
3. Detect deviation from constant risk
4. Move to Weibull, Cox, or piecewise hazard models

Rejecting the exponential model is often **informative**.

---

## 9. Churn interpretation

If exponential fits churn data:
- Users do not become more loyal over time
- Product shows no duration-based stickiness

If it fails:
- Duration dependence exists
- User behavior changes with tenure

---

## Final takeaway

$$
\boxed{
\text{Constant hazard is assumed not because we believe it, but because it is the simplest possible survival model.}
}
$$

All meaningful survival analysis studies how reality deviates from this baseline.
