---

title: "[선형대수] diagonalizability"  
date: 2024-10-13 19:30:00 +09:00  
categories: [ai, study]  
tags: [ ai, study, 선형대수, diagonalizability]  
math: true  

---

**선요약**  

`Diagonalizability` : nxn 행렬 A가 diagonalizable이면 A는 n개의 linearly independent eigenvector를 갖고 있다. 이를 확인하는 방법들은 다음과 같다.
`1.Split` :
`2.Multiplicity` :
`3.`

<br/>

---

# **Diagonalizability**

어떤 행렬이 diagonalizable하다는 것은, 그 행렬을 적절한 basis로 변환했을 때 대각 행렬(diagonal matrix)로 표현될 수 있음을 의미한다. diagonalizability는 복잡한 행렬 계산을 단순화하고, 행렬의 eigenvalue와 eigenvector를 분석하는 중요한 방법이다.

<br/>

# **1. Split**

Split은 선형대수에서 행렬의 특성 다항식(characteristic polynomial)이 모든 eigenvalue에 대해 분해되는 상태를 의미한다. characteristic polynomial이 split된다는 것은, polynomial이 $( t - \lambda_1 $), $( t - \lambda_2 $) 등의 형태로 eigenvalue들로 나눠진다는 뜻이다.

예를 들어, $( A $)라는 행렬의 characteristic polynomial이 $( p(t) = (t - 1)(t - 2)^2 $)라고 할 때, 이 polynomial은 eigenvalue $(1$)과 $(2$)를 가지며, eigenvalue $(2$)는 중복도(Multiplicity)가 2인 값이다. 이 경우, polynomial이 분해되므로 split되었다고 말할 수 있습니다.

행렬이 diagonalizable하면 split이 되지만, split이 된다고 Diagonalizability를 보장하진 않는다. (eigenvector가 부족할 수 있으므로)

<br/>

## **2. (Algebraic) Multiplicity**

Algebraic multiplicity는 eigenvalue의 중복도를 의미한다. 쉽게 말해, characteristic polynomial에서 각 eigenvalue가 몇 번 등장하는지를 나타낸다.

예를 들어, 다음과 같은 characteristic polynomial을 가진 행렬에서:

$$
p(t) = (t - 3)^2(t - 5)
$$

여기서 eigenvalue $(3$)은 두 번 등장하므로 대수적 중복도(algebraic multiplicity)가 2이다. eigenvalue $(5$)는 한 번 등장하므로 algebraic multiplicity가 1이다.

diagonalizability를 판단할 때 중요한 것은, eigenvalue의 algebraic multiplicity와 고유공간(eigenspace)의 차원(기하적 중복도, geometric multiplicity)이 일치하는지 여부이다. 이를 통해 행렬의 diagonalizability를 알 수 있다.

<br/>

## **3. Algebraic Multiplicity & Geometric Multiplicity**

eigenvalue의 algebraic multiplicity와 geometric multiplicity는 diagonalizability를 판단하는 중요한 요소이다. 여기서 algebraic multiplicity는 eigenvalue가 characteristic polynomial에서 몇 번 등장하는지 나타내고, geometric multiplicity는 해당 eigenvalue에 대한 eigenspace의 차원을 나타냅니다.

각 eigenvalue $(\lambda_i)$에 대해 algebraic multiplicity $(m_i$)와 고유공간 $(E_{\lambda_i}$)의 차원 $(d_i$)을 비교한다. Theorem 5.7에 따르면, 항상 $(1 \leq d_i \leq m_i$)이다. 만약 $(T$)가 diagonalizable하다면, 이 inequality가 $(d_i = m_i$)로 성립하고, 그 경우 $(T$)는 eigenvector로 이루어진 완전한 basis를 가진다.

따라서 eigenvalue $(\lambda_i$)의 algebraic multiplicity와 eigenspace의 차원이 일치하는지 여부에 따라 diagonalizability 여부가 결정된다.

<br/>

## **4. Diagonalizability Test**

Diagonalizability를 테스트하는 스텝은 다음과 같다.

**Step 1: Characteristic Polynomial**  
먼저 주어진 행렬의 characteristic polynomial을 계산한다. characteristic polynomial은 다음과 같이 구할 수 있다:

$$
\det(A - \lambda I) = 0
$$

여기서 $(\lambda$)는 eigenvalue, $(A$)는 행렬, $(I$)는 단위 행렬.

**Step 2: Split**  
characteristic polynomial이 모든 eigenvalue에 대해 split되는지 확인한다. characteristic polynomial이 split되지 않는다면, 행렬은 diagonalizable할 수 없다.

**Step 3: Eigenvalue의 Algebraic & Geometric Multiplicity 비교**  
eigenvalue의 algebraic multiplicity가 $(n - \text{rank}(T - \lambda I)$)와 일치하는지 확인한다. eigenvalue의 multiplicity가 1인 경우는 이 조건이 자동으로 충족된다. ( $(text{rank}(T - \lambda I)$)) 가 자동적으로 n - 1 이 되고 결과적으로 equality가 보장되므로)

**Step 4: Eigenvector**  
마지막으로 eigenvector들로 이루어진 basis를 찾는다. 모든 고유공간에서 선형 독립인 eigenvector들이 존재하면, 이 행렬은 diagonalizable입니다.

<br/>

### **예시**

다음은 diagonalizability를 테스트하는 예시이다.

$$
A = \begin{pmatrix} 3 & 1 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 4 \end{pmatrix}
$$

1. **Step 1: Characteristic Polynomial**  
   $A$의 특성 다항식은 $\det(A - \lambda I)$를 통해 구할 수 있다.

   $$
   \det(A - \lambda I) = (3 - \lambda)^2(4 - \lambda)
   $$

   eigenvalue는 $(\lambda_1 = 4$), $(\lambda_2 = 3$) (Multiplicity 2).

2. **Step 2: Split**  
   characteristic polynomial이 두 eigenvalue로 분리되었으므로, split된다고 말할 수 있다.

3. **Step 3: 각 Eigenvalue의 Algebraic & Geometric Multiplicity 비교**  
   - $(\lambda_1 = 4$): algebraic multiplicity는 1이고, eigenspace의 차원은 $(3 - \text{rank}(A - 4I)) = (3 - 2) = 1$)로서 일치한다.
   - $(\lambda_2 = 3$): algebraic multiplicity는 2이지만, eigenspace의 차원은 $(3 - \text{rank}(A - 3I)) = (3 - 2) = 1$)로 일치하지 않으므로 diagonalizable하지 않다.

4. **결론**  
   $(\lambda_2 = 3$)에서 algebraic multiplicity와 geometric multiplicity가 다르므로, 이 행렬은 diagonalizable하지 않다.

<br/>

[Linear Algebra Stephen H. Friedberg - section 5.2](https://g.co/kgs/PAu2zpL)