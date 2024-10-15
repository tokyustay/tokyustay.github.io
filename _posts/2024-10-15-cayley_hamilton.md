---

title: “[선형대수] invariant subspace, block matrix, cyclic subspace, Cayley-Hamilton theorem”  
date: 2024-10-15 11:18:00 +09:00  
categories: [ai, study]  
tags: [ ai, study, 선형대수, Invariant Subspace, Block Matrix, Cyclic Subspace, Cayley-Hamilton]  
math: true  

---

**선요약**

`Invariant Subspace`: 주어진 선형 변환 $T$가 특정 부분공간을 그 자체로 변환한다면, 이 부분공간을 $T$-Invariant Subspace이라고 한다. 

`Block Matrix`: 행렬을 하위 행렬들로 나누어 표현하는 방법으로, 불변 부분공간을 통해 얻은 행렬을 더 간단하게 분석할 수 있게 한다.

`Cyclic Subspace`: 벡터와 선형 변환을 반복적으로 적용해서 생성되는 부분공간을 말하며, 행렬의 중요한 성질을 파악하는 데 유용하다.

`Cayley-Hamilton theorem`: 모든 행렬은 자신의 특성 다항식을 만족한다는 이론이다.

<br/>
<br/>

# **1. Invariant Subspace**

Invariant Subspace는 주어진 선형 변환 $T$가 벡터 공간 $V$의 부분공간 $W$에 대해 다음 조건을 만족할 때 $T$-Invariant Subspace라고 한다:

$$
T(W) \subseteq W
$$

쉽게 말해, $W$의 모든 벡터 $v \in W$에 대해 $T(v)$도 여전히 $W$에 속한다는 것이다. 예를 들어, $xy$-평면이나 eigenvalue에 대응하는 eigenvector들의 subspace는 불변 Invariant Subspace가 될 수 있다.

### **예시**

Invariant Subspace를 찾는 것은 diagonalizablilty을 확인하는 중요한 과정이다. 예를 들어, 행렬 $A$가 주어졌을 때 그 eigenvalue에 대응하는 eigenvector들로 이루어진 subspave는 $A$-Invariant Subspace가 된다.

다음과 같은 선형 변환 $T : \mathbb{R}^3 \to \mathbb{R}^3$를 생각해보자:

$$
T(x, y, z) = (x + y, y - z, z)
$$

여기서, $xy$-평면은 $T$-Invariant Subspace가 될 수 있다. 왜냐하면 $xy$-평면에 속한 모든 벡터는 변환 후에도 여전히 $xy$-평면에 남기 때문이다.

<br/>

<br/>

# **2. Block Matrix**

Block Matrix은 행렬을 더 작은 하위 행렬들로 나누어 분석하는 방법이다. 주어진 행렬이 Invariant Subspace을 갖는 경우, 이 행렬을 블록 대각 행렬로 표현할 수 있다. 예를 들어, 다음과 같은 Block Matrix을 생각해보자:

$$
A = \begin{pmatrix} A_1 & A_2 \\ O & A_3 \end{pmatrix}
$$

여기서 $A_1$과 $A_3$는 각각 서로 독립적인 Invariant Subspace를 나타내고, 이 불변 Invariant Subspace들은 서로 상호작용하지 않는다. 따라서 이러한 블록 구조는 행렬의 성질을 더 쉽게 분석할 수 있게 도와준다.

행렬 $A$가 nxn일 때, $A_1$ 이 kxk이면 $A_3$ $(n-k)(n-k)$ 가 되고 $A_2$는 $kx(n-k)$ 가 된다. $O$는 영행렬

<br/>

# **3. Cyclic Subspace**

Cyclic Subspace는 선형 변환 $T$와 벡터 $v$가 주어졌을 때, $v$와 그에 대한 $T$의 반복적인 작용으로 생성되는 부분공간이다. 이를 수학적으로 표현하면 다음과 같다:

$$
W = \text{span}\{v, T(v), T^2(v), \dots \}
$$

이 순환 부분공간은 대각화 가능성 여부를 판단하거나, 행렬의 구조를 분석하는 데 유용하다. 특히 순환 부분공간이 작을수록 행렬의 성질을 분석하기가 쉬워진다.

### **예시**

다항식 공간 $P_3(\mathbb{R})$에서 도함수 연산자 $D$를 적용하면, Cyclic Subspace를 만들 수 있다. 예를 들어 $f(x) = x^2 + x + 1$에서 Cyclic Subspace을 고려하면:

$$
W = \text{span}\{f(x), D(f(x)), D^2(f(x))\} = \text{span}\{x^2 + x + 1, 2x + 1, 2\}
$$

이처럼 polynomial의 도함수로 이루어진 Cyclic Subspace도 중요한 분석 도구가 될 수 있다.

<br/>

# **4. Cayley-Hamilton theorem**

Cayley-Hamilton theorem은 모든 행렬이 자신의 characteristic polynomial을 만족한다는 이론이다. $T$라는 행렬이 주어졌을 때 그 characteristic polynomial은 다음과 같다:

$$
p(t) = \det(T - tI)
$$

이 정리는 $T$에 대해 다음과 같은 성질을 보장한다:

$$
p(T) = 0
$$

즉, 특성 다항식에 행렬 $T$를 대입했을 때 결과는 영행렬이 된다는 것이다. 예를 들어, $T = \begin{pmatrix} 2 & 1 \\ 0 & 3 \end{pmatrix}$ 라는 행렬에 대해 특성 다항식을 계산하면:

$$
p(t) = (2 - t)(3 - t) = t^2 - 5t + 6
$$

이제 $T$에 대해 Cayley-Hamilton theorem을 적용하면 다음이 성립한다:

$$
T^2 - 5T + 6I = 0
$$

이를 통해 행렬의 고차 계산을 단순화할 수 있다.

<br/>


[Linear Algebra Stephen H. Friedberg - section 5.4](https://g.co/kgs/PAu2zpL)