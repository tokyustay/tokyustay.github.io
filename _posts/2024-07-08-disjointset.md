---
title: "[자료구조] disjoint set: make-set, find-set, union"
date: 2024-07-08 16:23:00 +09:00
categories: [algorithm, review]
tags:
  [
    algorithm,
    disjoint set,
    union-find
  ]
math: true
---

# **선요약**

**Disjoint Set** : 서로 독립인 집합들을 관리하는 자료 구조. Kruskal 알고리즘 등에서 사용됨

- **Make-Set(x)** : 새로운 원소 x를 포함하는 새로운 집합을 생성
- **Find-Set(x)** : 원소 x가 속한 집합의 대표를 반환
- **Union(x, y)** : 원소 x와 y가 속한 두 집합을 하나로 합침

<br/>
<br/>

# **Disjoint Set**

## **Make-Set**

새로운 원소 x를 포함하는 새로운 집합을 생성. 초기 parent는 x

```python
class DisjointSet:
    def __init__(self):
        self.parent = {}
        self.rank = {}

    def make_set(self, x):
        self.parent[x] = x
        self.rank[x] = 0
```

## **Find-Set**

원소 x가 속한 집합의 대표를 반환. parent가 다른 원소로 union에서 결정된 상태일 경우 recursive하게 parent를 찾아 경로 압축

```python
    def find_set(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find_set(self.parent[x])  # 경로 압축
        return self.parent[x]
```

## **Union**

원소 x와 y가 속한 두 집합을 하나로 합침. 동시에 parent를 바꿈

```python
    def union(self, x, y):
        root_x = self.find_set(x)
        root_y = self.find_set(y)

        if root_x != root_y:
            if self.rank[root_x] > self.rank[root_y]:
                self.parent[root_y] = root_x
            elif self.rank[root_x] < self.rank[root_y]:
                self.parent[root_x] = root_y
            else:
                self.parent[root_y] = root_x
                self.rank[root_x] += 1
```

## **전체 코드**

```python
class DisjointSet:
    def __init__(self):
        self.parent = {}
        self.rank = {}

    def make_set(self, x):
        self.parent[x] = x
        self.rank[x] = 0

    def find_set(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find_set(self.parent[x])  # 경로 압축
        return self.parent[x]

    def union(self, x, y):
        root_x = self.find_set(x)
        root_y = self.find_set(y)

        if root_x != root_y:
            if self.rank[root_x] > self.rank[root_y]:
                self.parent[root_y] = root_x
            elif self.rank[root_x] < self.rank[root_y]:
                self.parent[root_x] = root_y
            else:
                self.parent[root_y] = root_x
                self.rank[root_x] += 1

# 예시 사용법
ds = DisjointSet()
elements = [1, 2, 3, 4, 5]

for elem in elements:
    ds.make_set(elem)

ds.union(1, 2)
ds.union(3, 4)
ds.union(2, 3)

print("1과 5가 같은 집합에 속하는가?", ds.find_set(1) == ds.find_set(5))  # False
print("1과 4가 같은 집합에 속하는가?", ds.find_set(1) == ds.find_set(4))  # True
```
