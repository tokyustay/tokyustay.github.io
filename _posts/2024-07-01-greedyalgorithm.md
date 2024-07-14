---
title: "[알고리즘] greedy algorithm"
date: 2024-07-01 12:57:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    greedy algorithm,
  ]
math: true
---

**선요약**

`Greedy Algorithm` : 매 단계에서 가장 좋아 보이는 선택을 반복적으로 하는 방법

- `Optimal Substructure Property`: 최적 해가 부분 문제의 최적 해로 구성
- `Greedy Choice Property`: 각 단계에서 지역적으로 최적의 선택이 전체적으로도 최적의 해를 보장

<br/>
<br/>

# **Greedy Algorithm**

Greedy Algorithm은 매 단계에서 가장 좋아 보이는 선택을 반복적으로 하여 문제를 해결하는 방법. 이 방법은 최적 부분 구조와 그리디 선택 속성을 만족하는 문제에 효과적

- 최적 부분 구조:
  - 문제의 최적 해가 부분 문제의 최적 해로 구성됨
- 그리디 선택 속성:
  - 각 단계에서 가장 좋아 보이는 선택이 전체적으로도 최적의 해를 보장
