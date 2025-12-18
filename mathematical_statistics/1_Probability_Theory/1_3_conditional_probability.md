## 1.3 Conditional Probabilitu
- Now, when we want to find the probability $P(A)$ of an event $A$ occurring, we consider how the prior knowledge that event $B$ has occurred changes $P(A)$.
- The definition of the conditional probability $P(A\vert B)$, that is, the probability of $A$ occurring given that $B$ has occurred, is as follows:

#### Definition 1.1 Conditional probability
Let events A and B be defined on the sample space S. The conditional probability of event A occurring, given that event B has occurred, is
$$
P(A\vert B) = frac{P(A\cap B)}{P(B)}
$$

B가 일어났다는 것을 알게 되면 $B^C$에 포함되는 실험결과들은 관찰이 불가능하므로 전체 표본공간은 $B$로 국한. 이떄 조건부 확률 $P(A\vert B)$는 $P(A\cap B)$의 새로운 표본공간의 확률, $P(B)$에 대한 상대적 크기를 의미.

#### Example
두 개의 동전을 던졌을 때 표본공간 $S=\\{HH,HT,TH,TT\\}$는 4개의 원소로 구성. 각 원소는 동일한 확률 1/4. 이제 첫 번째 동전이 앞면(H)이라는 조건하에서 두 개의 동전이 모두 앞면(H)일 조건부 확률을 구해보자.
$$
P(A\cap B\vert A) = \frac{P(A\cap B)}{P(A)}
& = \frac{P{HH}}{P{HH,HT}}
& = \frac{\frac{1}{4}}{\frac{1}{2}}
$$

다음으로, 조건부 확률로부터 유래하는 몇 개의 중요한 정리와 그에 따른 예들을 살펴보자.

#### Definition 1.2 전확률 공식
사건 $B_1, B_2, ..., B_k$는 상호 배반이며 $(B_i \cap B_j = \emptyset , i=j)$, $\bigcup_{i=1}^{k}B_i=S$라고 하자.
이때 임의의 사건 $A$에 대해,
$$
P(A)=\sum_{i=1}^{k}P(B_i)P(A\vert B_i)
$$

다음의 정리 1.3은 베이지안 통계이론의 기초가 되는 베이즈 정리.

#### Definition 1.3 베이즈 정리
사건 $B_1, B_2, ..., B_k$는 상호 배반이며 $(B_i \cap B_j = \emptyset , i=j)$, $\bigcup_{i=1}^{k}B_i=S$라고 하자.
이때 사건 $A$가 일어났다는 조건하에서 사건 $B_j$가 일어날 확률은
$$
P(B_j\vert A) = \frac{P(B_j)P(A\vert B)}{\sum_{i=1}^{k}P(B_i)P(A\vert B)}
$$

#### Example
어떤 질병 $A$에 대한 양성(+)과 음성(-)반응을 나타내는 검사방법이 있다. 이 검사방법이 실제로 질병이 있을 경우 양성 반응을 나타낼 확률이 $P(+\vert A)=0.95$이며
질병이 없을 경우에 양성반응을 나타낼 확률이 $P(+\vert A^C)=0.10$이라고 한다.
그런데 어떤 집단에서 무작위추출한 사람이 질병을 가지고 있을 확률은 $P(A)=0.01$이라고 한다.
이제 어떤 사람이 검사반응에서 양성(+)을 나타냈을 때, 그 사람이 실제로 질병 $A$를 가졌을 확률 $P(A\vert +)$는 다음과 같다.
$$
P(A\vert +) = \frac{P(A \cap +)}{P(+)}
& = \frac{P(+\vert A)P(A)}{P(+\vert A)P(A)+P(+\vert A^C)P(A^C)}
& = \frac{0.95\times0.01}{0.95\times0.01 + 0.10\times 0.99}
& = 0.088
$$

어떤 사건 $A$가 일어났다는 사실이 사건 $B$가 일어날 확률에 영향을 미치지 않는, 또는 반대인 경우를 생각해보자. 이를 확률을 사용하여 표현하면 $P(B\vert A)=P(B)$ 또는 $P(A\vert B)=P(A)$이 된다. 이런 성징릉 갖는 두 사건을 서로 **indepedent**라고 한다.
이떄 $P(A\cap B)=P(B)P(A\vert B)$를 활용하면 독립사건 $A$와 $B$에 대해 아래와 같은 정의를 이끌어낼 수 있다.

#### Definition 1.5 Indenpendence
두 사건 A와 B가
$$
 $P(A\cap B)=P(B)P(AB)$
$$
를 만족시키면 서로 **indepedent**라고 한다.


## 1.4 Combinatorics
유한개의 원소로 이루어진 표본공간을 형성하는 실험들 중에 많은 경우 모든 가능한 원소가 발생할 확률이 동일하다고 가정할 수 있다.
이런 경우 어떤 사건 A가 일어날 확률은, $n(A)$를 사건 $A$가 발생할 수 있는 경우의 수, 그리고 $N$을 모든 가능한 경우의 수라고 할때, $P(A)=n(A)/N$으로 정의하는 것이 타당.
여기에서는 이러한 확률 계산에 도움이 되는 '경우의 수'계산의 근본이 되는 순열과 조합을 간략히 다룸.

- multiplication rule: 사건 $A$가 일어나는 방법이 $m$가지이고 그 각각에 대해 사건 $B$가 일어나는 방법이 $n$가지이면, 사건 $A$와 $B$가 동시에 일어나는 방법은 $m\times n$가지 이다.
- permutation: 서로 다른 $n$개의 원소 중에서 $r$개를 선택하여 순서있게 늘어놓는 것을 $n$개에서 $r$개 택한 permutation이라고 하며 늘어놓는 경우의 수를 $_{n}P_{r}$
