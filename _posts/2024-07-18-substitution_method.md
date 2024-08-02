---
title: "[알고리즘] substitution method"
date: 2024-07-18 10:52:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    substitution method,
  ]
math: true
---

**선요약**

`치환법 (Substitution Method)` : `분할 정복(Divide & Conquer)` 기법에서 사용되는 알고리즘의 재귀식의 `시간 복잡도`를 분석하는 방법. upper bound를 추측하고 귀납법을 통해 검증하여 찾는다


<br/>
<br/>

# **Substitution Method**

알고리즘의 재귀 관계를 분석하여 점근적 상한(Asymptotic Upper Bound)을 찾는 기법. 이 방법은 재귀 관계를 점근적 표기법으로 표현하고, 이를 수학적 귀납법을 통해 검증

## **단계**

1. **추측 (Guessing)**:
   - 재귀 관계의 해가 될 것 같은 점근적 상한을 추측합니다.

2. **귀납법 적용 (Applying Induction)**:
   - 추측한 점근적 상한을 수학적 귀납법으로 검증합니다.


## **예시**

다음과 같은 재귀 관계를 고려

$
T(n) = 2T\left(\frac{n}{2}\right) + n
$

1. **추측 (Guessing)**

$T(n) = O(n \log n)$ 이라고 추측. 즉, $T(n) \leq c n \log n$ 이 되는 상수 $c$ 가 존재한다고 가정

2. **귀납법 적용 (Applying Induction)**

수학적 귀납법을 사용하여 추측을 검증. 귀납 가정을 세워 $T(k) \leq c k \log k$ 가 모든 $k < n$ 에 대해 성립한다고 가정. 이 가정을 사용하여 $T(n)$ 을 검증


$\begin{align*}$

<br/>

$T(n) = 2T\left(\frac{n}{2}\right) + n $

<br/>

$ \leq 2 \left( c \frac{n}{2} \log \frac{n}{2} \right) + n <br/>

$  = c n \log \frac{n}{2} + n $<br/>

$  = c n (\log n - \log 2) + n $<br/>

$  = c n \log n - c n \log 2 + n $<br/>

$  \leq c n \log n - c n + n $<br/>

$  = c n \log n - (c - 1) n$<br/>

$\end{align*}$<br/>


3. **검증**

상수 $c$ 가 충분히 크다면, $c n \log n - (c - 1) n \leq c n \log n$ 을 만족. 따라서, $T(n) \leq c n \log n$ 이 성립함

```python
def T(n):
    if n == 1:
        return 1
    else:
        return 2 * T(n // 2) + n

# 점근적 상한 검증
import math

def verify_guess(n, c):
    return T(n) <= c * n * math.log(n, 2)

# 예시 사용법
n = 16
c = 1  # 상수를 설정
print(f"T({n}) = {T(n)}")
print(f"verify_guess({n}, {c}) = {verify_guess(n, c)}")
```
