---
title: "[프리드버그 선형대수] 6.2 the gram-schmidt orthogonalization process and orthogonal complements"
date: 2024-10-27 10:02:00 +09:00  
categories: [ai, study]  
tags: [ ai, study, 선형대수]  
math: true  

---

# **6.2 The Gram-Schmidt Orthogonalization Process and Orthogonal Complements**

---

**선 요약**

이 장에서는 **직교 정규 기저**와 **그람-슈미트 직교화 과정**을 다룬다.  

- **직교 정규 기저 (Orthonormal Basis)**:  
  벡터 공간 \( V \)의 기저가 **직교(orthogonal)**하면서 각 벡터의 **길이(norm)**가 1인 경우를 말한다. 즉, 직교 정규 기저는 다음 조건을 만족한다:  
  \[
  \langle v_i, v_j \rangle = 0 \quad (i \neq j), \quad \|v_i\| = 1 \quad \forall i.
  \]

- **그람-슈미트 직교화 과정 (Gram-Schmidt Process)**:  
  선형 독립인 벡터 집합을 입력으로 받아 **직교 집합** 또는 **직교 정규 기저**를 생성하는 알고리즘이다. 이를 통해 벡터 공간의 구조를 더 명확하고 계산하기 쉬운 형태로 변환할 수 있다.

---

### Theorem

**Theorem 6.3 (Orthogonal Representation)**

벡터 공간 \( V \)와 직교 집합 \( S = \{v_1, v_2, \dots, v_k\} \)가 주어졌을 때, \( y \in \text{span}(S) \)라면 다음과 같이 표현된다:

\[
y = \sum_{i=1}^k \frac{\langle y, v_i \rangle}{\|v_i\|^2} v_i.
\]

> **증명**:  
> \( y \)를 \( S \)의 선형 결합으로 표현하면:  
> \[
> y = \sum_{i=1}^k a_i v_i.
> \]
> \( v_j \)와 내적하면 \( a_j = \frac{\langle y, v_j \rangle}{\|v_j\|^2} \)가 성립한다.

---

**Theorem 6.4 (Gram-Schmidt Process)**

유한 차원 내적 공간 \( V \)와 선형 독립 집합 \( S = \{w_1, w_2, \dots, w_n\} \)가 주어졌을 때, \( S \)를 직교 집합 \( S' = \{v_1, v_2, \dots, v_n\} \)로 변환할 수 있다. 과정은 다음과 같다:

1. **첫 번째 벡터**:  
   \[
   v_1 = w_1.
   \]

2. **두 번째 이후의 벡터**:  
   \[
   v_k = w_k - \sum_{j=1}^{k-1} \frac{\langle w_k, v_j \rangle}{\|v_j\|^2} v_j, \quad \text{for \( 2 \leq k \leq n \)}.
   \]

3. **정규화**: 직교 집합을 정규화하여 **직교 정규 기저**를 생성한다:
   \[
   u_i = \frac{v_i}{\|v_i\|}.
   \]

---

**Theorem 6.5 (Representation in an Orthonormal Basis)**

\( V \)가 유한 차원 내적 공간이고 \( \beta = \{v_1, v_2, \dots, v_n\} \)가 \( V \)의 **직교 정규 기저**라면, \( x \in V \)에 대해:

\[
x = \sum_{i=1}^n \langle x, v_i \rangle v_i.
\]

---

**Theorem 6.6 (Orthogonal Projection)**

\( W \)가 \( V \)의 부분공간이고 \( y \in V \)라면, 다음을 만족하는 **유일한 벡터** \( u \in W \)와 \( z \in W^\perp \)가 존재해서:

\[
y = u + z.
\]

여기서 \( u \)는 \( W \)에 대한 \( y \)의 **직교 투영**이며:  
\[
u = \sum_{i=1}^k \langle y, v_i \rangle v_i \quad (\{v_1, v_2, \dots, v_k\} \text{는 \( W \)의 직교 정규 기저}).
\]

---

**Theorem 6.7 (Dimension and Orthogonal Complements)**

벡터 공간 \( V \)와 부분공간 \( W \subseteq V \)에 대해:

1. \( W \)는 **직교 보완 공간** \( W^\perp \)를 가지며:
   \[
   \dim(V) = \dim(W) + \dim(W^\perp).
   \]

2. \( W^\perp \)는 \( W \)와 직교하는 모든 벡터들의 집합으로 정의된다:
   \[
   W^\perp = \{ x \in V \mid \langle x, y \rangle = 0 \, \forall y \in W \}.
   \]

---

### **Definition**

**직교(Orthogonal) 집합**: 벡터 공간 \( V \)에서 벡터 집합 \( S = \{v_1, v_2, \dots, v_n\} \)가 직교한다는 것은:  
\[
\langle v_i, v_j \rangle = 0 \quad (i \neq j).
\]

**직교 정규(Orthonormal) 집합**: 벡터 집합이 직교하며, 각 벡터의 길이가 1인 경우:  
\[
\|v_i\| = 1 \quad \text{and} \quad \langle v_i, v_j \rangle = 0 \quad (i \neq j).
\]

**직교 보완 공간 (Orthogonal Complement)**: 부분집합 \( S \subseteq V \)에 대해, \( S \)와 직교하는 모든 벡터들의 집합:  
\[
S^\perp = \{ x \in V \mid \langle x, y \rangle = 0 \, \forall y \in S \}.
\]

---

## **결론**

이 장에서는 **그람-슈미트 직교화 과정**을 통해 선형 독립 집합을 **직교 집합**으로 변환하는 방법을 학습했으며, 이를 정규화해 **직교 정규 기저**를 생성하는 방법과 기하학적 의미를 배웠다. 

<br/>

[Linear Algebra Stephen H. Friedberg - chapter 1](https://g.co/kgs/PAu2zpL)