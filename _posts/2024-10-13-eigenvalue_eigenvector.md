---
title: "[선형대수] eigenvalue & eigenvector"
date: 2024-10-13 16:30:00 +09:00
categories: [ai, study]
tags:
  [
    ai,
    study,
    선형대수,
    eigenvalue,
    eigenvector
  ]
math: true
---

**선요약**

`고유벡터 (Eigenvector)` **:** 선형 변환을 받았을 때 그 방향이 변하지 않는 벡터.

`고유값 (Eigenvalue)` **:** 그 벡터의 크기를 바꾸는 값.



<br/>
<br/>

# **Eigenvalue & Eigenvector**

어떤 선형 변환 $( T $)을 받았을 때(행렬이 벡터에 작용할 때) 방향이 변하지 않고 크기만 변화하는 벡터를 eigenvector, 그 크기 변화를 나타내는 값을 eigenvalue라고 한다.

정의는 아래와 같다:

선형 변환 $( T $)에 대해, 만약 다음을 만족하는 $( \mathbf{v} \neq \mathbf{0} $) 벡터가 존재하면:

$$
T(\mathbf{v}) = \lambda \mathbf{v}
$$

여기서 $( \lambda $)는 eigenvalue, $( \mathbf{v} $)는 해당 eigenvalue에 대응하는 eigenvector이다.

$( T $)를 행렬 $( A $)로 표현하고 식을 넘기면,

$$
(A - \lambda I)v = 0
$$

여기서 $( A $)는 행렬, $( \lambda $)는 eigenvalue, $( v $)는 eigenvector를 나타내며, $( I $)는 단위 행렬이다.

이를 통해 eigenvalue와 eigenvector를 찾을 수 있다.

- $( (A - \lambda I)v = 0 $)에서 벡터 $( v $)는 0이 아닌 eigenvector이다( $( v = 0 $) 인경우 너무 trivial한 solution이기 때문). 이때 행렬 $(A - \lambda I = 0$)이 가역 이라면(역행렬이 존재한다면), 양쪽에 역행렬을 곱해서 $( v = 0$)이라는 결론이 나오므로 **행렬 $( A - \lambda I = 0$)는 가역이 될 수 없어야 한다.** 그래야 비가역적이기 때문에 eigenvector가 0이 아님을 보장하기 때문. **즉, $( \det(A - \lambda I) = 0 $)이 되어야 한다.**
- $( \det(A - \lambda I) = 0 $)를 통해 구한 각 eigenvalue에 대해 $( A - \lambda I $)의 Null space를 구한다. Null space는 이 행렬에 의해 0 벡터로 보내지는 모든 벡터들의 공간으로 eigenvector v가 된다.
- 행렬 $( A $)는 정사각 행렬이다.

<br/>

### **예시**

3차원 공간에서 다음과 같은 행렬 $( A $)가 있다고 가정:

$$
A = \begin{pmatrix} 1 & 3 \\ 4 & 2 \end{pmatrix}
$$

1. **Eigenvalue 계산**  
   eigenvalue는 $( \det(A - \lambda I) = 0 $) 식을 풀어 구한다.

   $$ 
   \det\begin{pmatrix} 1-\lambda & 3 \\ 4 & 2-\lambda \end{pmatrix} = (1-\lambda)(2-\lambda) - (4 \cdot 3) = \lambda^2 - 3\lambda - 10 = 0 
   $$

   이 식의 근을 구하면, $( \lambda = -2 $) 또는 $( \lambda = 5 $).

2. **Eigenvector 계산**  
   각 eigenvalue에 대해 $( A - \lambda I $)의 Null space를 구한다. 예를 들어, $( \lambda = -2 $)일 때:

   $$ 
   A - (-2)I = \begin{pmatrix} 3 & 3 \\ 4 & 4 \end{pmatrix}
   $$

   이 행렬을 풀어 보면 고유벡터는 $ \mathbf{v} = \begin{pmatrix} 1 \\ -1 \end{pmatrix} $.

<br/>

# **파이썬에서**

Python의 `numpy` 라이브러리를 사용하면 쉽게 고유값과 고유벡터를 계산할 수 있다.

```python
import numpy as np

# 행렬 정의
A = np.array([[1, 3], [4, 2]])

# 고유값 및 고유벡터 계산
eigenvalues, eigenvectors = np.linalg.eig(A)

print("고유값:", eigenvalues)
print("고유벡터:\n", eigenvectors)
```

위 코드를 실행하면 다음과 같은 결과를 얻을 수 있습니다:
```bash
고유값: [-2.  5.]
고유벡터:
 [[ 0.70710678  0.4472136 ]
 [-0.70710678  0.89442719]]
```

<br/>

[Linear Algebra Stephen H. Friedberg - section 5.2](https://g.co/kgs/PAu2zpL)

[혁펜하임, 고윳값 & 고유 벡터](https://youtu.be/xDARfmKauuA?si=W7Zm-vLPYKp57P1m)
