## Boole’s Inequality (Finite Case)

### Statement

Let $A_1, A_2, \dots, A_n$ be events in a probability space $(\Omega, \mathcal{F}, P)$.  
Then

$$
P\!\left(\bigcup_{i=1}^{n} A_i\right) \le \sum_{i=1}^{n} P(A_i).
$$

---

### Proof

Define events $B_1, B_2, \dots, B_n$ as follows:

$$
B_1 = A_1,
$$

$$
B_k = A_k \setminus \bigcup_{i=1}^{k-1} A_i \quad \text{for } k = 2, \dots, n.
$$

Then:

- The events $B_1, B_2, \dots, B_n$ are pairwise disjoint.
- Their union equals the union of the original events:

$$
\bigcup_{k=1}^{n} B_k = \bigcup_{k=1}^{n} A_k.
$$

By finite additivity of probability for disjoint events,

$$
P\!\left(\bigcup_{k=1}^{n} A_k\right)
= P\!\left(\bigcup_{k=1}^{n} B_k\right)
= \sum_{k=1}^{n} P(B_k).
$$

Since $B_k \subseteq A_k$ for each $k$, by monotonicity of probability,

$$
P(B_k) \le P(A_k).
$$

Therefore,

$$
P\!\left(\bigcup_{k=1}^{n} A_k\right)
= \sum_{k=1}^{n} P(B_k)
\le \sum_{k=1}^{n} P(A_k).
$$

This completes the proof.

## Bonferroni Inequality (Finite Case)

### Statement (first-order Bonferroni bounds)

Let $A_1, A_2, \dots, A_n$ be events in a probability space $(\Omega,\mathcal{F},P)$. Then

- **Upper bound (Boole / union bound)**

$$
P\!\left(\bigcup_{i=1}^{n} A_i\right) \le \sum_{i=1}^{n} P(A_i).
$$

- **Lower bound (Bonferroni inequality)**

$$
P\!\left(\bigcup_{i=1}^{n} A_i\right) \ge \sum_{i=1}^{n} P(A_i)\;-\;\sum_{1\le i<j\le n} P(A_i\cap A_j).
$$

---

### Proof (finite case)

Define

$$
S(\omega)=\sum_{i=1}^{n}\mathbf{1}_{A_i}(\omega),
$$

where $\mathbf{1}_{A_i}$ is the indicator of $A_i$.  
Note that

$$
\mathbf{1}_{\cup_{i=1}^n A_i}(\omega)=\mathbf{1}_{\{S(\omega)\ge 1\}}.
$$

Also define

$$
T(\omega)=\sum_{1\le i<j\le n}\mathbf{1}_{A_i\cap A_j}(\omega).
$$

Now fix $\omega\in\Omega$. Let $k=S(\omega)$ be the number of events that occur at $\omega$.

- If $k=0$, then $\mathbf{1}_{\cup A_i}(\omega)=0$ and $\sum_i \mathbf{1}_{A_i}(\omega)-\sum_{i<j}\mathbf{1}_{A_i\cap A_j}(\omega)=0$.
- If $k\ge 1$, then $\mathbf{1}_{\cup A_i}(\omega)=1$, and
  $$
  \sum_{i=1}^n \mathbf{1}_{A_i}(\omega)=k,\qquad
  \sum_{1\le i<j\le n}\mathbf{1}_{A_i\cap A_j}(\omega)=\binom{k}{2}.
  $$
  Hence
  $$
  k-\binom{k}{2} \le 1 \quad \text{for all } k\ge 1,
  $$
  because $k-\binom{k}{2}=k-\frac{k(k-1)}{2}\le 1$ (check: equality at $k=1,2$, and it decreases for $k\ge 3$).

Therefore, for every $\omega$,

$$
\mathbf{1}_{\cup_{i=1}^n A_i}(\omega)
\ge
\sum_{i=1}^{n}\mathbf{1}_{A_i}(\omega)
-
\sum_{1\le i<j\le n}\mathbf{1}_{A_i\cap A_j}(\omega).
$$

Taking expectations on both sides and using linearity of expectation gives

$$
P\!\left(\bigcup_{i=1}^{n} A_i\right)
=
\mathbb{E}\left[\mathbf{1}_{\cup_{i=1}^n A_i}\right]
\ge
\sum_{i=1}^{n}\mathbb{E}\left[\mathbf{1}_{A_i}\right]
-
\sum_{1\le i<j\le n}\mathbb{E}\left[\mathbf{1}_{A_i\cap A_j}\right].
$$

Since $\mathbb{E}[\mathbf{1}_{A}]=P(A)$, we obtain

$$
P\!\left(\bigcup_{i=1}^{n} A_i\right)
\ge
\sum_{i=1}^{n} P(A_i)
-
\sum_{1\le i<j\le n} P(A_i\cap A_j),
$$

which is the (first-order) Bonferroni inequality.
