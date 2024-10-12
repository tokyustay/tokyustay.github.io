---
title: "[선형대수] linearly Independent and dependent"
date: 2024-10-08 19:18:00 +09:00
categories: [ai, study]
tags:
  [
    ai,
    study,
    선형대수
  ]
math: true
---

**선요약**

`선형 독립 (Linear Independence)` **:** 벡터 집합에서 어떤 벡터도 다른 벡터들의 선형 결합으로 표현될 수 없을 때, 그 집합을 Linear Independence라고 한다.

`선형 종속 (Linear Dependence)` **:** 벡터 집합에서 적어도 하나의 벡터가 다른 벡터들의 선형 결합으로 표현될 수 있을 때, 그 집합을 Linear Dependence라고 한다.

<br/>
<br/>



# **Linear Independence**

Linear Independence는 벡터 집합에서 각 벡터가 다른 벡터들의 선형 결합으로 표현될 수 없을 때를 말한다. 좀 더 구체적으로, 벡터 집합 $( \{ \mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n \} $)이 선형 독립이라면, 다음의 등식이 성립할 때:

$$
c_1 \mathbf{v}_1 + c_2 \mathbf{v}_2 + \ldots + c_n \mathbf{v}_n = \mathbf{0}
$$

여기서 $( c_1, c_2, \ldots, c_n $)이 모두 0일 때만 이 식이 성립할 경우, Linearly Independent 집합이다. 직관적으로 두 개의 2차원 벡터가 같은 직선 위에 있으면 서로 적절히 배수하여 합이 0이 될 수 있지만, 약간이라도 다른 방향을 가지면 두 벡터 모두 0이어야만 합이 0이 된다.

### **예시**

3차원 공간에서 다음 세 벡터가 있다고 가정하자:

$$
\mathbf{v}_1 = \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}, \quad
\mathbf{v}_2 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}, \quad
\mathbf{v}_3 = \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
$$

이 벡터들은 서로 직교하며, 어떠한 벡터도 다른 벡터들의 선형 결합으로 표현될 수 없다. 따라서 이 벡터 집합은 Linearly Independent하다.

<br/>

# **Linear Dependence**

반대로, Linear Dependence는 벡터 집합에서 적어도 하나의 벡터가 다른 벡터들의 선형 결합으로 표현될 수 있을 때를 말한다. 다시 말해, 위의 Linear Independence의 정의에서 모든 $( c_i = 0 $)인 경우 외에도 해가 존재하는 경우를 의미한다.

### **예시**

다시 3차원 공간에서 다음 세 벡터를 고려하자:

$$
\mathbf{v}_1 = \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}, \quad
\mathbf{v}_2 = \begin{pmatrix} 2 \\ 4 \\ 6 \end{pmatrix}, \quad
\mathbf{v}_3 = \begin{pmatrix} 3 \\ 6 \\ 9 \end{pmatrix}
$$

이 경우, $( \mathbf{v}_2 = 2\mathbf{v}_1 $)이고, $( \mathbf{v}_3 = 3\mathbf{v}_1 $)이므로, 이 벡터들은 Linearly Dependent하다.

<br/>

# **Linear Independence, Linear Dependence 판단 방법**

Linear Independence와 Linear Dependence을 판단하는 일반적인 방법은 행렬의 Rank를 이용하는 것이다. 벡터 집합을 행렬의 row로 놓았을 때, 그 행렬의 Rank가 벡터의 수와 같으면 Linear Independence, 그렇지 않으면 Linear Dependence이다.

**Rank**

행렬의 Rank는 행렬의 Linear Independence인 row 또는 column의 최대 개수를 의미한다. 이를 통해 벡터 집합의 선형 독립성을 판단할 수 있다.

### **예시**

다음 행렬을 고려하자:

$$
A = \begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{pmatrix}
$$

이 행렬의 Rank는 3으로, 이는 벡터 $( \mathbf{v}_1, \mathbf{v}_2, \mathbf{v}_3 $)가 Linearly Independent함을 나타낸다.

반면, 다음 행렬의 Rank을 계산해보자:

$$
B = \begin{pmatrix}
1 & 2 & 3 \\
2 & 4 & 6 \\
3 & 6 & 9 \\
\end{pmatrix}
$$

이 행렬의 Rank은 1로, 이는 벡터 $( \mathbf{v}_1, \mathbf{v}_2, \mathbf{v}_3 $)가 Linearly Dependent함을 의미한다.

<br/>

# **파이썬에서**

파이썬의 `numpy` 라이브러리를 사용하여 벡터 집합의 선형 독립성을 확인할 수 있다. 다음은 이를 구현한 간단한 예제이다.

```python
import numpy as np

def is_linearly_independent(vectors):
    matrix = np.array(vectors).T
    rank = np.linalg.matrix_rank(matrix)
    return rank == len(vectors)

# 선형 독립인 벡터 집합
vectors_independent = [
    [1, 0, 0],
    [0, 1, 0],
    [0, 0, 1]
]

# 선형 종속인 벡터 집합
vectors_dependent = [
    [1, 2, 3],
    [2, 4, 6],
    [3, 6, 9]
]

print("선형 독립:", is_linearly_independent(vectors_independent))  # 출력: True
print("선형 종속:", is_linearly_independent(vectors_dependent))    # 출력: False
```

<br/>

[Linear Algebra Stephen H. Friedberg - section 5.1](https://g.co/kgs/PAu2zpL)
[혁펜하임, 선형 독립과 기저](https://youtu.be/mOOI4-BfjGQ?si=HydO3dh0RhdYnBpl)