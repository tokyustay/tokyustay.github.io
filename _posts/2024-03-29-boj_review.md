---
title: "boj review - sort, key, lambda, sys, dictionary, set"
date: 2024-03-26 23:38:00 +09:00
categories: [algorithm, boj]
tags:
  [
    10814번,
    18870번
  ]
---

# 요약

- 딕셔너리 시간복잡도 O(1), 리스트 O(N)
- for문 등 간단한 알고리즘은 시간복잡도에 컷될 확률이 높다

# 10814 나이순 정렬

- note : 2차원 배열 정렬, sort, key, lambda

```python
import sys
input = sys.stdin.readline

n = int(input())

arr = []

for i in range(n) :
    arr.append(list(input().split()))

arr.sort(key = lambda x:int(x[0])) # x[0]를 키값으로 정렬

for i in arr :
    print(*i)
```
예제 입력
```text
3
21 Junkyu
21 Dohyun
20 Sunyoung
```
예제 출력
```text
20 Sunyoung
21 Junkyu
21 Dohyun
```

# 18870 좌표 압축

- note : 딕셔너리 정렬, 리스트-딕셔너리 시간복잡도, set

```python
import sys
input = sys.stdin.readline

n = int(input())

arr = list(map(int, input().split()))

set_arr = sorted(list(set(arr))) # set = 집합으로 만들기(중복 제거)

dic = {set_arr[i]:i for i in range(len(set_arr))}

for i in arr :
    print(dic[i], end=" ")

# dictionary = 시간복잡도 O(1)
```
예제 입력
```text
5
2 4 -10 4 -9
```
예제 출력
```text
2 3 0 3 1
```