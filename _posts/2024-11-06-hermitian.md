---
title: "[프리드버그 선형대수] 6.4 normal and self-adjoint operators"
date: 2024-11-06 6:32:00 +09:00  
categories: [ai, study]  
tags: [ ai, study, 선형대수]  
math: true  

---

# **6.4 Normal and Self-Adjoint Operators**

**선요약**  

이 장에서는 **정규 연산자(Normal Operators)**와 **자기 수반 연산자(Self-Adjoint Operators)**의 정의와 성질, 그리고 이들의 대각화 가능성을 다룬다.

<br/>

# **Theorem**  

**Definition**

- **정규 연산자 (Normal Operator)**:  
  내적 공간 $V$ 위의 선형 연산자 $T$가 정규일 조건은 다음과 같다:  
  $$
  TT^* = T^*T.
  $$

- **자기 수반 연산자 (Self-Adjoint Operator)**:  
  내적 공간 $V$ 위의 선형 연산자 $T$가 자기 수반일 조건은 다음과 같다:  
  $$
  T = T^*.
  $$  

- 행렬 $A$에 대해서는 $A = A^*$가 자기 수반의 조건이 된다.

**Lemma (Eigenvectors and Adjoint Operators)**

$T$가 선형 연산자이고 $T$의 고유 벡터 $v$가 존재하면, $T^*$도 같은 고유값에 대해 고유 벡터 $v$를 가진다.  

> **증명**:  
> $T(v) = \lambda v$라 하자.  
> $$0 = \langle (T - \lambda I)v, x \rangle = \langle v, (T - \lambda I)^*(x) \rangle = \langle v, (T^* - \bar{\lambda}I)x \rangle$$.  
> 따라서 $v$는 $T^* - \bar{\lambda}I$ 의 영공간에 속하며, 이는 $T^*$도 $v$를 고유 벡터로 가진다는 것을 의미한다.

<br/>

**Theorem 6.14 (Schur's Theorem)**

유한 차원 내적 공간 $V$ 위의 선형 연산자 $T$에 대해 $T$의 특성 다항식이 분할되면, $V$에는 $T$에 대한 직교 정규 기저 $\beta$가 존재하여 $[T]_{\beta}$는 상삼각 행렬이 된다.

> **증명**:  
> 귀납법으로 차원을 기준으로 증명한다.  
> - $n = 1$인 경우, 자명하게 성립한다.  
> - $T$의 $T^*$가 고유 벡터 $z$를 가진다고 가정하자. 그러면 부분공간 $W = \text{span}(\{z\})$와 $W^\perp$에 대해 Schur's Theorem을 귀납적으로 적용한다.  
> - $W^\perp$에 대해 $T$의 제한 연산자가 상삼각 행렬임을 보이고, 전체 공간 $V$에서 $T$는 상삼각 행렬이 된다.  

**Definition**:  

내적 공간 $V$ 위의 선형 연산자 $T$에 대해 $T$가 **정규 (normal)**일 조건은 다음과 같다:  

$$
TT^* = T^*T
$$

또한 $n \times n$ 실수 또는 복소 행렬 $A$가 정규일 조건은:  

$$
AA^* = A^*A.
$$

이때, Theorem 6.10에 의해 $T$ 는 **$[T]_\beta$ 가 정규일 때** 정규이다. 여기서 $\beta$ 는 $V$ 의 직교 정규 기저이다.

<br/>

**Theorem 6.15 (Properties of Normal Operators)**  

$V$ 위의 정규 연산자 $T$에 대해 다음이 성립한다:  

1. $\|T(x)\| = \|T^*(x)\| \quad \forall x \in V$.  
2. $T - cI$는 정규이다 ($c \in F$).  
3. $T$의 고유 벡터는 $T^*$의 고유 벡터이기도 하다.  
4. 서로 다른 고유값에 대응하는 고유 벡터들은 직교한다.

> **증명**:  
> (1)  
> $$\|T(x)\|^2 = \langle T(x), T(x) \rangle = \langle T^*T(x), x \rangle = \|T^*(x)\|^2$$  
> (3)  
> $T(x) = \lambda x$ 일 때, $T^*(x) = \bar{\lambda}x$ 이므로 동일한 고유 벡터를 가진다.  
> (4)  
> 서로 다른 고유값 $\lambda_1 \neq \lambda_2$에 대해:  
> $$\lambda_1 \langle x_1, x_2 \rangle = \langle T(x_1), x_2 \rangle = \langle x_1, T^*(x_2) \rangle = \bar{\lambda}_2 \langle x_1, x_2 \rangle.$$
> 따라서 $\langle x_1, x_2 \rangle = 0$.

<br/>

**Theorem 6.16 (Normal Operators and Orthogonal Bases)** 

복소 내적 공간 $V$ 위의 선형 연산자 $T$가 정규일 필요충분조건은 $T$의 고유 벡터들로 이루어진 직교 정규 기저가 존재하는 것이다.

> **증명**:  
> Schur의 정리를 이용해 $[T]_{\beta}$ 를 상삼각 행렬로 만든다.  
> $T$ 가 정규이므로 $[T]_{\beta}$와 $[T^*]_{\beta}$ 는 모두 상삼각 행렬이며 서로 수반 관계에 있다.  
> 따라서 $[T]_{\beta}$ 는 대각 행렬이 되어야 하므로, $T$는 대각화 가능하며 직교 정규 기저를 가진다.

**Definition**:

내적 공간 $V$ 위의 선형 연산자 $T$에 대해 $T$가 **자기 수반 (self-adjoint)**일 조건은 다음과 같다:  

$$
T = T^*.
$$  

$n \times n$ 실수 또는 복소 행렬 $A$가 자기 수반일 조건은 $A = A^*$이다.

이때 직교 정규 기저 $\beta$ 에 대해 $[T]_\beta$ 가 자기 수반이면 $T$는 자기 수반이다. 실수 행렬의 경우, 이는 $A$가 **대칭 행렬**임을 의미한다.

**Lemma (Properties of Self-Adjoint Operators)**:  
 
$T$가 유한 차원 내적 공간 $V$ 위의 자기 수반 연산자일 때 다음이 성립한다:

1. **(a)** $T$의 모든 고유값은 실수이다.  
2. **(b)** $V$가 실수 내적 공간이라면, $T$의 특성 다항식은 실수에서 분할된다.

> **증명**:  
> **(a)** $T(x) = \lambda x$일 때, $T$가 자기 수반이므로:  
> $$\lambda x = T(x) = T^*(x) = \bar{\lambda}x.$$  
> 따라서 $\lambda = \bar{\lambda}$이고, $\lambda$는 실수이다.  
>  
> **(b)** $\dim(V) = n$이라 하고, $\beta$를 $V$의 직교 정규 기저라 하자.  
> 이때 $A = [T]_\beta$ 는 자기 수반이므로 $A$는 실수 대칭 행렬이다.  
> $T_A$ 를 $\mathbb{C}^n$ 위의 선형 연산자로 정의하면 $T_A$는 자기 수반이므로, 모든 고유값이 실수이다.  
> 따라서 $T$의 특성 다항식은 실수에서 분할된다.

<br/>

**Theorem 6.17 (Self-Adjoint Operators and Diagonalization)**  
  
실수 내적 공간 $V$ 위의 선형 연산자 $T$가 자기 수반일 필요충분조건은 $T$에 대한 고유 벡터들로 구성된 직교 정규 기저가 존재하는 것이다.

> **증명**:  
> Schur의 정리에 의해 $T$ 는 상삼각 행렬 $[T]_{\beta}$ 로 표현된다.  
> $T = T^*$ 이므로 $[T]_{\beta}$ 는 대각 행렬이다.  
> 따라서 $T$의 고유 벡터들이 직교 정규 기저를 형성한다.

<br/>

### **결론**  

이 장에서는 **정규 연산자**와 **자기 수반 연산자**의 성질과 대각화 가능성을 학습하였다. 특히, 정규 연산자는 서로 다른 고유값에 대응하는 고유 벡터들이 직교하며, 자기 수반 연산자는 실수 고유값을 가지며 대각화 가능함을 보였다.  

<br/>

[Linear Algebra Stephen H. Friedberg - Chapter 6.4](https://g.co/kgs/PAu2zpL)  
