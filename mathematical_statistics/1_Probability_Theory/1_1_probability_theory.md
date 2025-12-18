## 1.1 Introduction
To describe a phenomenon(or characteristcs), we often use mathematical models to represent or predict it. 

### Deterministic model
For example, when you drop an object from a certain height, its speed is given by $v = gt$, where $g$ is gravity and $t$ is the time. If the conditions remain the same, repeating the experiment will always produce the same speed. This kind of model is called a "deterministic model."


### Probability model
In contrast, there are some phenomena where the outcome depends on chance each time we repeat the experiment. For example, if you flip a coin 10 times, the number of times it lands on heads is determined by probability. In this case, the previous deterministic model does not apply. To study such situations, we use probability models.

### Terminology
Let's define some basic terminology:
- Experiment: **a procedure** carried out to observe the outcome of a certain phenomenon.
- Sample space: the set of **all possible outcomes** of an experiment.
- Event: any **subset** of the sample space.

### Examples
#### Example 1 (Finite discrete sample space, Bernoulli trials):
- Experiment: Flip a coin 3 times.
- Sample space ($S$): $S = \\{HHH, HHT, HTH, THH, HTT, THT, TTH, TTT\\}$.
- (This is the set of all possible ordered sequences of heads and tails for 3 tosses.)
- Event example ("exactly 2 heads appear"): $A = \\{HHT, HTH, THH\\}$.
- (A subset of $S$ determined by a condition.)
- If we define a random variable $X$ as "the number of heads appearing," then the sample space for $X$ becomes $S_X = \\{0, 1, 2, 3\\}$.
- Event example for $X$ ("at least one head appears"): $A_X = \\{1, 2, 3\\}$.

#### Example 2 (Infinite discrete sample space, Geometric distribution process):
- Experiment: Flip a coin repeatedly until the first tail appears.
- Sample space ($S$): $S = \\{T, HT, HHT, HHHT, \ldots\\}$
- Here, the number of possible outcomes is infinite.
- Event example ("the first tail appears on the third flip"): $A = \\{HHT\\}$

#### Example 3 (Continuous sample space, Lifetime/Survival analysis):
Consider measuring the lifespan of a machine. The observed value can be any non-negative real number, so the appropriate sample space is $S = \\{x \mid 0 \leq x < \infty\\}$.  
- Event: "The machine works for at least 20 hours" is $A = \\{x \mid x \geq 20\\}$.  
This type of example is often referred to as a *continuous sample space* (specifically, an example from lifetime or survival analysis) in probability theory.

### Definitions
#### Definition 1.1 intersection, union

Let $A$ and $B$ be events in the same sample space. We define:
- **Intersection ($A \cap B$):** the event that both $A$ and $B$ occur.
- **Union ($A \cup B$):** the event that at least one of $A$ or $B$ occurs.

#### Definition 1.2 mutually exclusive
If two events $A$ and $B$ are defined on the same sample space $S$ and have no outcomes in common, that is, $A \cap B = \emptyset$, then $A$ and $B$ are said to be **mutually exclusive**.

#### Definition 1.3 Complement
Let $A$ be an event defined on a sample space $S$. The **complement** of $A$, denoted by $A^C$, is the set of all elements in $S$ that are not in $A$; in other words, $A^C$ consists of all outcomes where $A$ does not occur.

### Examples
- In the earlier coin toss example, the event "at least one head appears" and the event "all tails" are mutually exclusive (they have no outcomes in common).
- The complement of the event "an even number appears" (when rolling a die) is the event "an odd number appears".

### Recap
- objective of models, deterministic moodel, probability model
- terminology: experiment, sample space, event
- definitions: intersection, union, mutually exclusive, complement
