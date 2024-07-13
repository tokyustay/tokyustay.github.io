---
title: "[자료구조] tree, forest, graph"
date: 2024-06-22 11:46:00 +09:00
categories: [algorithm, review]
tags:
  [
    data structure,
    tree,
    graph,
    forest
  ]
math: true
---


# **선요약**

**Tree, Forest, Graph** : 자료 구조의 기본 개념들로, 다양한 형태와 용도로 사용됨.

| 용어 | 정의 | 특징 | 주요 용도 |
| --- | --- | --- | --- |
| **Tree** | 무방향 그래프 중 비순환적이며 연결된 그래프 | 루트에서 시작하여 자식 노드로 확장 | 파일 시스템, 데이터베이스 |
| **Forest** | 무방향 그래프 중 비순환적인 그래프 | 여러 개의 Tree로 구성 | 그래프 이론, 알고리즘 |
| Rooted Tree | 특정 노드가 루트로 지정된 Tree | 방향성이 있음 | 트리 탐색 알고리즘 |
| **Undirected Graph** | 방향이 없는 그래프 | 간선에 방향이 없음 | 네트워크, 관계 그래프 |
| Binary Tree | 각 노드가 최대 두 개의 자식을 가질 수 있는 Rooted Tree | 이진 탐색, 힙 자료 구조 | 이진 탐색 트리, 힙 |
| **Complete Binary Tree** | 모든 레벨이 꽉 찬 Binary Tree | 마지막 레벨을 제외하고 완전히 채워짐 | 힙 자료 구조 |

<br/>
<br/>

# **Tree**

**Tree** : undirected 그래프 중 acyclic이며 연결된 그래프

- 각 노드는 부모와 자식 관계로 연결.
- 사이클이 없음.
- 주요 용도: 파일 시스템, 데이터베이스.

```markdown
# Tree 예시
       A
      / \
     B   C
    / \   \
   D   E   F
```

# **Forest**

**Forest** : undirected 그래프 중 acyclic 그래프

- 여러 개의 Tree로 구성.
- 루트가 없음.
- 주요 용도: 그래프 이론, 알고리즘.

```markdown
# Forest 예시
       A            G
      / \          / \
     B   C        H   I
    / \   \          / \
   D   E   F        J   K
```

# **Rooted Tree**

**Rooted Tree** : 특정 노드가 루트로 지정된 Tree

- 방향성이 있음.
- 주요 용도: 트리 탐색 알고리즘.

```markdown
# Rooted Tree 예시
       A
      / \
     B   C
    / \   \
   D   E   F
```

# **Undirected Graph**

**Undirected Graph** : 방향이 없는 그래프

- 간선에 방향이 없음.
- 노드 간의 관계를 나타냄.
- 주요 용도: 네트워크, 관계 그래프.

```markdown
# Undirected Graph 예시
    A -- B
    |    |
    C -- D
```

# **Binary Tree**

**Binary Tree** : 각 노드가 최대 두 개의 자식을 가질 수 있는 Rooted Tree

- 왼쪽 자식과 오른쪽 자식으로 구분.
- 주요 용도: 이진 탐색 트리, 힙 자료 구조.

```markdown
# Binary Tree 예시
       A
      / \
     B   C
    / \   \
   D   E   F
```

# **Complete Binary Tree**

**Complete Binary Tree** : 모든 레벨이 꽉 찬 Binary Tree

- 마지막 레벨을 제외하고 완전히 채워짐.
- 주요 용도: 힙 자료 구조.

```markdown
# Complete Binary Tree 예시
       A
      / \
     B   C
    / \  / \
   D  E F   G
```
