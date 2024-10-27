---
title: "[프리드버그 선형대수] 6.2 the gram-schmidt orthogonalization process and orthogonal complements"
date: 2024-10-27 10:02:00 +09:00  
categories: [ai, study]  
tags: [ ai, study, 선형대수]  
math: true  

---

# **6.2 The Gram-Schmidt Orthogonalization Process and Orthogonal Complements**

**선 요약**

이 장에서는 **직교 정규 기저**와 **그람-슈미트 직교화 과정**을 다루며, 직교 정규 기저를 활용한 벡터 표현과 직교 보완 공간의 개념을 설명한다.  

- **직교 정규 기저 (Orthonormal Basis)**:  
  벡터 공간 $V$의 기저가 **직교(orthogonal)**하면서 각 벡터의 **길이(norm)**가 1인 경우를 말한다. 즉, 직교 정규 기저는 다음 조건을 만족한다:  
  $$
  \langle v_i, v_j \rangle = 0 \quad (i \neq j), \quad \|v_i\| = 1 \quad \forall i.
  $$

- **그람-슈미트 직교화 과정 (Gram-Schmidt Process)**:  
  선형 독립인 벡터 집합을 입력으로 받아 **직교 집합** 또는 **직교 정규 기저**를 생성하는 알고리즘이다. 이를 통해 벡터 공간의 구조를 더 명확하고 계산하기 쉬운 형태로 변환할 수 있다.


### **Theorem**

**Theorem 6.3 (Orthogonal Representation)**

벡터 공간 $V$와 직교 집합 $S = \{v_1, v_2, \dots, v_k\}$가 주어졌을 때, $y \in \text{span}(S)$ 라면 다음과 같이 표현된다:

$$
y = \sum_{i=1}^k \frac{\langle y, v_i \rangle}{\|v_i\|^2} v_i.
$$

> **증명**:  
> $y$를 $S$의 선형 결합으로 표현하면:  
> $$y = \sum_{i=1}^k a_i v_i$$.
> $v_j$와 내적하면 $a_j = \frac{\langle y, v_j \rangle}{\|v_j\|^2}$ 가 성립한다.

**Theorem 6.4 (Gram-Schmidt Process)**

유한 차원 내적 공간 $V$ 와 선형 독립 집합 $ S = \{w_1, w_2, \dots, w_n\} $ 가 주어졌을 때, $S$ 를 직교 집합 $ S' = \{v_1, v_2, \dots, v_n\} $ 로 변환할 수 있다.

> **증명**:  
> 귀납법으로 증명한다.  
> 1. $ v_1 = w_1 $ 로 정의하면 $ v_1 \neq 0 $ 이다.  
> 2. $ k \geq 2 $ 일 때, $ v_k $ 를 다음과 같이 정의한다:  
>    $$v_k = w_k - \sum_{j=1}^{k-1} \frac{\langle w_k, v_j \rangle}{\|v_j\|^2} v_j$$.
>    $ v_k $ 가 직교 집합임을 보이기 위해, $ i < k $ 에 대해 $ \langle v_k, v_i \rangle = 0 $ 임을 확인한다.  
>    $$\langle v_k, v_i \rangle = \langle w_k, v_i \rangle - \sum_{j=1}^{k-1} \frac{\langle w_k, v_j \rangle}{\|v_j\|^2} \langle v_j, v_i \rangle = 0$$.
> 따라서 $ v_k $ 는 기존 벡터들과 직교하며, 이 과정을 반복하면 직교 집합 $ \{v_1, v_2, \dots, v_n\} $ 를 얻는다.

**Theorem 6.5 (Representation in an Orthonormal Basis)**

$ V $ 가 유한 차원 내적 공간이고 $ \beta = \{v_1, v_2, \dots, v_n\} $ 가 $ V $ 의 **직교 정규 기저**라면, $ x \in V $ 에 대해:

$$
x = \sum_{i=1}^n \langle x, v_i \rangle v_i.
$$

> **증명**:  
> $ \beta $ 가 직교 정규 기저이므로:  
> $ x $ 를 $ \beta $ 의 선형 결합으로 표현한다고 가정하자:  
> $$x = \sum_{i=1}^n c_i v_i$$.
> 양변을 $ v_j $ 와 내적하면:  
> $$\langle x, v_j \rangle = \left\langle \sum_{i=1}^n c_i v_i, v_j \right\rangle = c_j \|v_j\|^2 = c_j$$.
> 따라서 $ c_j = \langle x, v_j \rangle $ 이고, 이를 대입하면:  
> $$x = \sum_{i=1}^n \langle x, v_i \rangle v_i$$.

**Corollary (Linear Operator Representation)**

유한 차원 내적 공간 $ V $ 가 직교 정규 기저 $ \beta = \{v_1, v_2, \dots, v_n\} $ 를 가질 때, 선형 변환 $ T: V \to V $ 의 행렬 표현 $ A = [T]_{\beta} $ 는 다음과 같다:

$$
A_{ij} = \langle T(v_j), v_i \rangle.
$$

**Theorem 6.6 (Orthogonal Projection)**

$ W $ 가 $ V $ 의 부분공간이고 $ y \in V $ 라면, 다음을 만족하는 **유일한 벡터** $ u \in W $ 와 $ z \in W^\perp $ 가 존재해서:

$$
y = u + z.
$$

여기서 $ u $ 는 $ W $ 에 대한 $ y $ 의 **직교 투영**이며:  
$$
u = \sum_{i=1}^k \langle y, v_i \rangle v_i \quad (\{v_1, v_2, \dots, v_k\} \text{는 $ W $의 직교 정규 기저}).
$$

> **증명**:  
> 1. $ \{v_1, v_2, \dots, v_k\} $ 를 $ W $ 의 직교 정규 기저라고 하자.  
> 2. $ u \in W $ 를 다음과 같이 정의한다:  
>    $$u = \sum_{i=1}^k \langle y, v_i \rangle v_i$$.
> 3. $ z = y - u $ 라 하면, $ z $ 는 $ W^\perp $ 에 속함을 보인다.  
>    $$\langle z, v_j \rangle = \langle y - u, v_j \rangle = \langle y, v_j \rangle - \langle u, v_j \rangle = 0$$.
> 따라서 $ y = u + z $ 이며, $ u $ 와 $ z $ 는 유일하다.

**Corollary (Best Approximation Property)**

$ W \subseteq V $ 가 부분공간이고 $ y \in V $ 일 때, $ W $ 에 대한 $ y $ 의 직교 투영 $ u $ 는 다음을 만족한다:

$$
\|y - u\| \leq \|y - x\| \quad \forall x \in W.
$$

**Theorem 6.7 (Dimension and Orthogonal Complements)**

벡터 공간 $ V $ 와 부분공간 $ W \subseteq V $ 에 대해:

1. $ W $ 는 **직교 보완 공간** $ W^\perp $ 를 가지며:
   $$
   \dim(V) = \dim(W) + \dim(W^\perp).
   $$

2. $ W^\perp $ 는 $ W $ 와 직교하는 모든 벡터들의 집합으로 정의된다:
   $$
   W^\perp = \{ x \in V \mid \langle x, y \rangle = 0 \forall y \in W \}.
   $$

### **결론**

이 장에서는 **그람-슈미트 직교화 과정**을 통해 선형 독립 집합을 **직교 집합**으로 변환하는 방법과 **직교 정규 기저**를 만드는 방법을 배웠다. 또한 **직교 투영**과 **직교 보완 공간**을 활용해 벡터를 효율적으로 분해하는 이론을 학습했다.  

<br/>

[Linear Algebra Stephen H. Friedberg - chapter 1](https://g.co/kgs/PAu2zpL)
