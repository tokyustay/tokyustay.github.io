---
title: "[알고리즘] linear programming : simplex algorithm"
date: 2024-07-17 10:42:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    linear programming,
    simplex algorithm,
    optimization
  ]
math: true
---

**선요약**

`선형 계획법 (Linear Programming)` : 선형 함수의 최댓값 또는 최솟값을 찾는 최적화 문제

`Simplex Algorithm`: 선형 계획법 문제를 해결하는 대표적인 알고리즘

<br/>
<br/>

# **선형 계획법 (Linear Programming)**

주어진 제약 조건 하에서 선형 함수의 최댓값 또는 최솟값을 찾는 최적화 문제. 이는 중학교때 배운 최대 이익 문제라고 생각하면 쉬움. 이러한 Linear Programming은 Simplex Method나 Interior Point Method로 해결할 수 있다

<br/>

![lp](https://upload.wikimedia.org/wikipedia/commons/1/18/%EC%84%A0%ED%98%95_%EA%B3%84%ED%9A%8D%EB%B2%95.png)

<br/>

## Standard From

최적화할 원래 함수와 조건들

1. **목적 함수 (Objective Function)**:
   - 최적화하려는 대상, 일반적으로 최대화 또는 최소화하려는 선형 함수

2. **제약 조건 (Constraints)**:
   - 문제 해결 시 반드시 만족해야 하는 선형 부등식 집합

3. **비음수 조건 (Non-negativity Constraints)**:
   - 변수는 0 또는 양수이어야 함

예시는 다음과 같다

$
\begin{align*}
\text{Maximize } & z = 3x_1 + 2x_2 \\
\text{Subject to } & x_1 + x_2 \leq 4 \\
& 2x_1 + x_2 \leq 6 \\
& x_1 \geq 0, \ x_2 \geq 0
\end{align*}
$

## Slack Form

Standard Form의 부등식을 등식으로 만들기 위해 느슨한 변수(Slack variable)를 도입하는 형식. 위의 Standard Form을 Slack Form으로 변경하면

$
\begin{align*}
\text{Maximize } & z = 3x_1 + 2x_2 \\
\text{Subject to } & x_1 + x_2 + s_1 = 4 \\
& 2x_1 + x_2 + s_2 = 6 \\
& x_1, x_2, s_1, s_2 \geq 0
\end{align*}
$

# **Simplex Algorithm**

선형 계획법 문제를 해결하는 대표적인 방법으로, Standard Form에서 Slack Form으로 변경 후, 기저 변수의 교체를 반복하며 최적 해를 탐색한다


## **알고리즘 단계**

1. **초기 기저 변수 선택**:
   - 가능한 초기 기저 변수를 선택, Maximize 목적함수에서 coefficient값이 제일 큰 변수가 선택된다
2. **목적 함수 개선**:
   - Slack variable이 도임된 기저 변수가 포함된 부등식에서 기저 변수를 부등식 왼쪽에, 나머지 변수를 오른쪽으로 옮긴 후, 기저 변수의 coefficient가 1이 되도록 표현식을 만든다. 이 표현식을 목적 함수에 대입해 목적 함수를 개선한다
3. **기저 변수 교체**:
   - 새로운 기저 변수를 새로운 목적 함수에서 1번 단계와 동일하게 선택, 목적함수의 모든 변수의 coefficient가 음수가 될 때 까지 반복한다


```python
from scipy.optimize import linprog

# 목적 함수 계수
c = [-3, -2]  # linprog는 최소화를 수행하므로, 최대화 문제를 최소화로 변환

# 제약 조건 계수
A = [[1, 1], [2, 1]]
b = [4, 6]

# 비음수 조건
x0_bounds = (0, None)
x1_bounds = (0, None)

# 선형 계획 문제 해결
result = linprog(c, A_ub=A, b_ub=b, bounds=[x0_bounds, x1_bounds], method='simplex')

print('최적의 해:', result.x)
print('최대 이익:', -result.fun)
```
