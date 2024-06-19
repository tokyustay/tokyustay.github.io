---
title: "[알고리즘] binary search, bisect"
date: 2024-03-21 02:04:00 +09:00
categories: [algorithm, review]
tags:
  [
    binary search,
    bisect
  ]
---

# Binary Search

이진 탐색, **정렬되어 있는 리스트**에서 **탐색 범위를 절반씩 좁혀가며 데이터를 탐색**하는 방법
<br/>
<br/>
시간 복잡도는 O(log n)

## 재귀 방식

```python
def binary_search (array, target ,start, end) :
    if(start > end) :
        return None
    mid = (start + end) // 2
    if (array[mid] == target) : 
        return mid
    elif (array[mid] > target) :
        return binary_search (array, target, start, mid - 1)
    else :
        return binary_search (array, target, mid + 1, end)
    

n, target = list(map(int, input().split()))

array = list(map(int, input().split()))

result = binary_search(array, target, 0, n - 1)

if result == None :
    print('-1')
else : 
    print(result + 1)
```
input
```
10 7
1 3 5 7 9 11 13 15 17 19
```
result
```
4
```

## 반복문 방식

```py
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        if array[mid] == target :
            return mid
        elif array[mid] > target :
            start = mid - 1
        else :
            end = mid + 1
    return None
```

<br/>
<br/>
<br/>

# Bisect Library

파이썬의 이진탐색 라이브러리

```python
bisect_left(a, x) = 정렬된 배열 a에 x를 삽입할 가장 왼쪽 인덱스
bisect_right(a, x) = 정렬된 배열 a에 x를 삽입할 가장 오른쪽 인덱스
```

## Bisect 이용 범위 측정


```py
from bisect import bisect_left, bisect_right
import random

array = random.choices(range(0, 6), k=10)

array.sort()

print(array)

def count_by_range(array, left_value, right_value) :
    left_index = bisect_left(array, left_value)
    print(left_index)
    right_index = bisect_right(array, right_value)
    print(right_index)
    return right_index - left_index

length = count_by_range(array, 4, 4)

print(length)
```
result
```
[0, 1, 1, 1, 2, 3, 3, 4, 5, 5]
7
8
1
```