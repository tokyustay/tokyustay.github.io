---
title: "[알고리즘] master theorem"
date: 2024-06-18 09:46:56 +09:00
categories: [algorithm, review]
tags:
  [
    master theorem
  ]
math: true
---

# **선요약**

**마스터 정리(Master Theorem)** : 분할 정복(Divide & Conquer) 기법에서 사용되는 알고리즘의 재귀식의 시간 복잡도를 분석하는 방법. 다음과 같은 형태의 재귀식을 해결하는 데 사용됨

$$ 
T(n) = aT\left(\frac{n}{b}\right) + f(n) 
$$

여기서,
- $a \geq 1$ 과 $b > 1$ 은 상수
- $f(n)$ 은 주어진 함수

<br/>

# **Case별 마스터 정리**

1. **Case 1:**

   $$
   f(n) = O\left(n^{\log_b a - \epsilon}\right) 
   $$

   $$
   \text{for some } \epsilon > 0 
   $$

   이 경우,

   $$
   T(n) = \Theta\left(n^{\log_b a}\right) 
   $$

2. **Case 2:**

   $$
   f(n) = \Theta\left(n^{\log_b a}\right) 
   $$

   이 경우,

   $$
   T(n) = \Theta\left(n^{\log_b a} \log n\right) 
   $$

3. **Case 3:**

   $$
   f(n) = \Omega\left(n^{\log_b a + \epsilon}\right) 
   $$

   $$
   \text{for some } \epsilon > 0, \text{ and if } af\left(\frac{n}{b}\right) \leq cf(n) \text{ for some } c < 1 \text{ and sufficiently large } n 
   $$

   이 경우,

   $$
   T(n) = \Theta(f(n)) 
   $$

<br/>

#### **예제 1**

$$
T(n) = 2T\left(\frac{n}{2}\right) + n 
$$

여기서, $a = 2$, $b = 2$, $f(n) = n$

- $\log_b a = \log_2 2 = 1$
- $f(n) = n = \Theta(n^{\log_b a})$

이는 Case 2에 해당하므로:

$$
T(n) = \Theta(n \log n) 
$$

<br/>

#### **예제 2**

$$
T(n) = 3T\left(\frac{n}{4}\right) + n 
$$

여기서, $a = 3$, $b = 4$, $f(n) = n$

- $\log_b a = \log_4 3 \approx 0.793$
- $f(n) = n = \Omega(n^{\log_b a + \epsilon}) \text{ for } \epsilon \approx 0.207$

이는 Case 3에 해당하며, 추가 조건 $$af\left(\frac{n}{b}\right) \leq cf(n)$$을 만족하므로:

$$
T(n) = \Theta(n) 
$$

---