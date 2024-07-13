---
title: "[알고리즘] dynamic programming : assembly line scheduling & matrix chain multiplication"
date: 2024-06-26 12:22:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    dynamic programming,
    scheduling,
    matrix multiplication
  ]
math: true
---

# **선요약**

<br/>

**Dynamic Programming** : 동적 프로그래밍은 **최적 부분 구조(Optimal Substructure)**와 **겹치는 부분 문제(Overlapping Subproblems)** 속성을 가진 최적화 문제를 테이블을 사용하여 효율적으로 해결하는 방법

- **최적 부분 구조**: 문제의 최적 해가 부분 문제의 최적 해로 구성됨
- **겹치는 부분 문제**: 동일한 부분 문제가 반복해서 계산됨

<br/>

**예시 1 : Assembly Line Scheduling** : 여러 조립 라인에서 작업 시간과 전환 시간을 고려하여 전체 작업 시간을 최소화하는 문제

<br/>

![assembly](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F996259335A082E7513)

<br/>

**예시 2 : Matrix Chain Multiplication** : 행렬 곱셈 순서를 최적화하여 계산 비용을 최소화하는 문제

<br/>


$ (A_1(A_2(A_3A_4))) $

<br/>

$ (A_1((A_2A_3)A_4)) $

<br/>

$ ((A_1A_2)(A_3A_4)) $

<br/>

$ ((A_1(A_2A_3))A_4) $

<br/>

$ (((A_1A_2)A_3)A_4) $

<br/>

![matrixchain](https://i.makeagif.com/media/1-19-2023/mpXkc0.gif)


<br/>
<br/>

# **Assembly Line Scheduling Problem**

두 개의 조립 라인에서 각 작업 스테이션의 작업 시간과 라인 간 전환 시간이 주어졌을 때, 전체 작업 시간을 최소화하는 문제

## **점화식**

- $ T1[j] = \min(T1[j-1] + a[0][j], T2[j-1] + t[1][j-1] + a[0][j]) $
- $ T2[j] = \min(T2[j-1] + a[1][j], T1[j-1] + t[0][j-1] + a[1][j]) $


```python
def assembly_line(a, t, e, x):
    n = len(a[0])
    T1 = [0] * n
    T2 = [0] * n

    T1[0] = e[0] + a[0][0]
    T2[0] = e[1] + a[1][0]

    for j in range(1, n):
        T1[j] = min(T1[j-1] + a[0][j], T2[j-1] + t[1][j-1] + a[0][j])
        T2[j] = min(T2[j-1] + a[1][j], T1[j-1] + t[0][j-1] + a[1][j])

    T_min = min(T1[n-1] + x[0], T2[n-1] + x[1])

    return T_min

a = [[4, 5, 3, 2], [2, 10, 1, 4]]
t = [[0, 7, 4, 5], [0, 9, 2, 8]]
e = [10, 12]
x = [18, 7]

print("최소 작업 시간:", assembly_line(a, t, e, x))
```

# **Matrix Chain Multiplication Problem**

주어진 여러 행렬들을 전부 곱할 때 곱셈 순서를 최적화하여 계산 비용을 최소화하는 문제

## **점화식**

- $ m[i][j] = \min_{i \leq k < j} (m[i][k] + m[k+1][j] + p[i-1] \times p[k] \times p[j]) $


```python
def matrix_chain_order(p):
    n = len(p) - 1
    m = [[0 for _ in range(n)] for _ in range(n)]

    for L in range(2, n+1):
        for i in range(n-L+1):
            j = i + L - 1
            m[i][j] = float('inf')
            for k in range(i, j):
                q = m[i][k] + m[k+1][j] + p[i] * p[k+1] * p[j+1]
                if q < m[i][j]:
                    m[i][j] = q

    return m[0][n-1]

p = [30, 35, 15, 5, 10, 20, 25]
print("최소 행렬 곱셈 비용:", matrix_chain_order(p))
```
