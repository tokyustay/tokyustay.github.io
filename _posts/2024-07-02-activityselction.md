---
title: "[알고리즘] greedy algorithm : activity selection problem"
date: 2024-07-02 13:00:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    greedy algorithm,
    activity selection
  ]
math: true
---

# **선요약**

**Greedy Algorithm** : 매 단계에서 가장 좋아 보이는 선택을 반복적으로 하는 방법

**Activity Selection Problem** : 주어진 활동들 중 겹치지 않게 가장 많은 활동을 선택하는 문제

- Optimal Substructure Property와 Greedy Choice Property를 모두 만족하여 그리디 알고리즘으로 해결 가능

<br/>
<br/>

# **Activity Selection Problem**

## **문제 정의**

여러 활동이 시작 시간과 종료 시간이 주어졌을 때, 서로 겹치지 않게 최대한 많은 활동을 선택하는 문제. 남은 시간 중에서 가장 빨리 끝나는 활동을 선택하면 전체적으로 가장 많은 활동을 선택할 수 있음

## **점화식**

- 최적 부분 구조:
  - $f_m = \min \{ f_k : a_k \in S_{ij} \}$
  - $a_m$은 가장 빨리 끝나는 활동



```python
def recursive_activity_selector(s, f, k, n):
    m = k + 1
    while m < n and s[m] < f[k]:
        m += 1
    if m < n:
        return [m] + recursive_activity_selector(s, f, m, n)
    else:
        return []

def greedy_activity_selector(s, f):
    n = len(s)
    A = [0]
    k = 0
    for m in range(1, n):
        if s[m] >= f[k]:
            A.append(m)
            k = m
    return A

s = [0, 1, 3, 0, 5, 3, 5, 6, 8, 8, 2, 12]
f = [6, 4, 5, 7, 9, 9, 9, 10, 11, 12, 14, 16]
n = len(s)

print("Recursive activity selection:", recursive_activity_selector(s, f, 0, n))
print("Greedy activity selection:", greedy_activity_selector(s, f))
```

Activity Selection Problem의 시간 복잡도는 $O(n)$, activity가 정렬되어있지 않은 경우는 $O(n log n)$
