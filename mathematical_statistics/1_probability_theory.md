## 1.1 Introduction
- To describe a phenomenon(or characteristcs), we often use mathematical models to represent or predict it. 

### Deterministic model
For example, when you drop an object from a certain height, its speed is given by $v = gt$, where $g$ is gravity and $t$ is the time. If the conditions remain the same, repeating the experiment will always produce the same speed. This kind of model is called a "deterministic model."


### Probability model
In contrast, there are some phenomena where the outcome depends on chance each time we repeat the experiment. For example, if you flip a coin 10 times, the number of times it lands on heads is determined by probability. In this case, the previous deterministic model does not apply. To study such situations, we use probability models.

### Terminology
Let's define some basic terminology:
- Experiment: a procedure carried out to observe the outcome of a certain phenomenon.
- Sample space: the set of all possible outcomes of an experiment.
- Event: any subset of the sample space.

### Examples
(1)
- Experiment: Flip a coin 3 times.
- Sample space (S): $S = \\{HHH, HHT, HTH, THH, HTT, THT, TTH, TTT\\}$.
If we are interested in the event "exactly 2 heads appear," then the event set (A) is $A = \\{HHT, HTH, THH\\}$.
Alternatively, if we look at the number of heads that appear, the sample space becomes $S = \\{0, 1, 2, 3\\}$. For example, the event "at least one head appears" would be $A = \\{1, 2, 3\\}$.

(2) 
- Experiment: Flip a coin until tail appeared.
- $S = \\{T, HT, HHT, HHHT, ... \\}$
- like above, the number of elements can be infinite.
- in this case, if you consider the event like "tail appeared in third time", $A = \\{HHT\\}$

(3) 
Let's consider that you measure the lifespan of the machine. the observable number would be the non-negative real number. Therefore, appropriate sample space $S = \\{x\vert 0 \leq x \leq \infty\\}$
- works over 20h event: $A = \\{x\vert x \geq 20\\\}$

#### Definition 1.1
- Event A, B are defined in the same sample space.
- (1) intersection: event that A and B simultaneously included. $A\cap B$
- (2) union: event that A or B included. $A\cup B$