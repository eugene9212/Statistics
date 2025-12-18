# Chapter 1. Probability Theory
## 1.3 Conditional Probabilitu
- Now, when we want to find the probability $P(A)$ of an event $A$ occurring, we consider how the prior knowledge that event $B$ has occurred changes $P(A)$.
- The definition of the conditional probability $P(A\vert B)$, that is, the probability of $A$ occurring given that $B$ has occurred, is as follows:

#### Definition 1.1 Conditional probability
Let events A and B be defined on the sample space S. The conditional probability of event A occurring, given that event B has occurred, is
$$
P(A\vert B) = frac{P(A\cap B)}{P(B)}
$$

When we know that $B$ has occurred, any experimental outcomes contained in $B^C$ (the complement of $B$) are no longer possible to observe. Thus, the entire sample space is restricted to $B$. In this situation, the conditional probability $P(A\vert B)$ represents the probability of $A \cap B$ relative to the new sample space $B$; in other words, it describes how likely $A$ is, given that $B$ has already occurred, as a proportion of $P(B)$.

#### Example
When two coins are tossed, the sample space is $S=\\{HH, HT, TH, TT\\}$, consisting of 4 possible outcomes. Each outcome has an equal probability of 1/4. Now, let's find the conditional probability that both coins show heads (HH), given that the first coin shows heads (H).
$$
P(A\cap B\vert A) = \frac{P(A\cap B)}{P(A)}
& = \frac{P{HH}}{P{HH,HT}}
& = \frac{\frac{1}{4}}{\frac{1}{2}}
$$

Next, let's look at some important theorems that follow from conditional probability, along with related examples.

#### Definition 1.2 전확률 공식
Let $B_1, B_2, \dots, B_k$ be mutually exclusive events (i.e., $B_i \cap B_j = \emptyset$ for $i \neq j$) such that their union covers the entire sample space, $\bigcup_{i=1}^{k} B_i = S$. Then for any event $A$,
$$
P(A)=\sum_{i=1}^{k}P(B_i)P(A\vert B_i)
$$

The following theorem (1.3) is Bayes' theorem, which forms the foundation of Bayesian statistical theory.

#### Definition 1.3 Bayes' Theorem
Let $B_1, B_2, \dots, B_k$ be mutually exclusive events ($B_i \cap B_j = \emptyset$ for $i \ne j$) whose union covers the entire sample space, i.e., $\bigcup_{i=1}^{k} B_i = S$.
Then, the probability that event $B_j$ occurs given that event $A$ has occurred is
$$
P(B_j\vert A) = \frac{P(B_j)P(A\vert B)}{\sum_{i=1}^{k}P(B_i)P(A\vert B)}
$$

#### Example
Suppose there is a medical test for a disease $A$ that produces either a positive (+) or negative (–) result. The probability that the test yields a positive result when the person actually has the disease is $P(+\vert A)=0.95$.
The probability that the test yields a positive result when the person does *not* have the disease is $P(+\vert A^C)=0.10$.
Furthermore, suppose the probability that a randomly selected person from a certain population has the disease is $P(A)=0.01$.
Now, if a person tests positive (+), the probability that this person actually has disease $A$, i.e. $P(A\vert +)$, is given as follows:
$$
P(A\vert +) = \frac{P(A \cap +)}{P(+)}
& = \frac{P(+\vert A)P(A)}{P(+\vert A)P(A)+P(+\vert A^C)P(A^C)}
& = \frac{0.95\times0.01}{0.95\times0.01 + 0.10\times 0.99}
& = 0.088
$$

Let us now consider the case where the occurrence of event $A$ does not affect the probability of event $B$, or vice versa. In probability terms, this means $P(B\vert A) = P(B)$ or $P(A\vert B) = P(A)$. Two such events are said to be **independent**.

Using the definition $P(A\cap B) = P(B)P(A\vert B)$, we can define independence as follows for events $A$ and $B$:

#### Definition 1.5 Independence
Events $A$ and $B$ are
$$
 $P(A\cap B)=P(B)P(AB)$
$$
If this condition is satisfied, the two events are said to be **independent**.


## 1.4 Combinatorics
In many experiments that produce a finite sample space, it is reasonable to assume that all possible outcomes are equally likely. In such cases, the probability of an event $A$ can be defined as follows: If $n(A)$ is the number of ways event $A$ can occur, and $N$ is the total number of possible outcomes, then $P(A) = n(A)/N$.

Here, we briefly review permutations and combinations—fundamental counting methods that facilitate such probability calculations.

- Multiplication rule: If there are $m$ ways for event $A$ to occur, and for each of these there are $n$ ways for event $B$ to occur, then there are $m \times n$ ways for both $A$ and $B$ to occur together.
- Permutation: Choosing $r$ elements from $n$ distinct objects and arranging them in order is called a permutation of $n$ objects taken $r$ at a time, and the number of such arrangements is denoted by $_{n}P_{r}$.
