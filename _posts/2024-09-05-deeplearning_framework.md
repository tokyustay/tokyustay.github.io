---
title: "[딥러닝] 딥러닝 프레임워크 비교(pytorch, tensorflow, kears, jax)"
date: 2024-09-05 14:10:00 +09:00
categories: [ai, study]
tags:
  [
    pytorch,
    tensorflow,
    keras
  ]
---

**선요약**

`프레임워크` : 라이브러리, 모듈, 커뮤니티 지원 등 다양한 요소를 포함하여 개발자가 소프트웨어를 효율적이게 구축할 수 있도록 도와주는 종합적인 플랫폼

`PyTorch` : Meta에서 개발한 딥러닝 프레임워크. 동적 계산과 쉬운 디버깅, 직관적이고 Pythonic한 특징을 가짐

`TensorFlow` : Google에서 개발한 딥러닝 프레임워크. 정적 계산과 빠르고 강력한 `XLA` 컴파일러 사용으로 강력하지만 쉽지 않은 디버깅과 직관적이지 않은 특징을 가짐. 하지만 점차 XLA의 역할을 축소하고 직관적인 `keras`와 통합하며 난이도가 낮아졌다

`JAX` : Google에서 개발한 고성능 수학 연산 라이브러리. 기본적으로 함수형 프로그래밍 패러다임을 따르며, XLA를 활용하는데 최적화되어있다

`keras` : 직관적이고 사용하기 편한 딥러닝 라이브러리, TensorFlow와 통합되었다

`XLA` : Google에서 개발한 머신러닝 프레임워크에서 사용되는 도메인 특화 컴파일러(DSL). XLA(Accelerated Linear Algebra)는 특히 행렬과 벡터 연산을 가속화하기 위해 설계되었다

<br/>
<br/>

# **PyTorch**

PyTorch는 Meta에서 개발한 오픈 소스 딥러닝 프레임워크로, **동적 계산 그래프**를 지원한다. 이는 코드 실행 시점에 그래프가 생성되고 수정될 수 있어, 직관적이고 유연한 코딩이 가능하다. 이러한 특징 덕분에 디버깅이 용이하고, 연구 및 프로토타이핑에 널리 사용된다

**하지만 XLA 기반 계산보다 성능을 내지 못할 수 있고, 2.0부터 torch.compile을 도입해 해결을 시도했지만, 완전한 해결책이 되진 못했다**

- **OpenAI**는 2020년에 내부적으로 PyTorch를 표준화하여 사용하고 있으며, 이는 연구와 산업 모두에서 PyTorch의 입지를 높이고 있다

```python
import torch
import torch.nn as nn
import torch.optim as optim

# 간단한 선형 회귀 모델
class LinearRegressionModel(nn.Module):
    def __init__(self):
        super(LinearRegressionModel, self).__init__()
        self.linear = nn.Linear(1, 1)
    def forward(self, x):
        return self.linear(x)

model = LinearRegressionModel()
criterion = nn.MSELoss()
optimizer = optim.SGD(model.parameters(), lr=0.01)

# 데이터
x_train = torch.tensor([[1], [2], [3], [4]], dtype=torch.float32)
y_train = torch.tensor([[2], [4], [6], [8]], dtype=torch.float32)

# 모델 훈련
for epoch in range(10):
    optimizer.zero_grad()
    outputs = model(x_train)
    loss = criterion(outputs, y_train)
    loss.backward()
    optimizer.step()
```

<br/>

# **TensorFlow**

TensorFlow는 Google에서 개발한 오픈 소스 딥러닝 프레임워크로, **정적 계산 그래프**를 기반으로 한다. 이는 컴파일 타임에 그래프가 결정되고 최적화되어, 모델의 효율적인 실행과 배포에 유리하다. 이러한 특성 때문에 모바일 및 임베디드 기기와 같은 여러 환경에서도 높은 성능을 발휘한다

Google의 지원으로 **TensorFlow Serving**, **TensorFlow Lite**, **TensorFlow.js** 등 다양한 도구를 제공하여 웹, 모바일, 임베디드 기기 등 여러 플랫폼에서의 배포를 지원하며, 이는 산업분야에서 TensorFlow가 선호되는 이유이다

**하지만 쉽지 않은 디버깅으로 연구자들에게 환영받지 못했으며, 이를 2.0부터 Eager Execution을 도입하여 동적 그래프도 지원하며, Keras와의 통합으로 개선하였다**

**이러한 개선은 오히려 TensorFlow만의 장점을 지우게 되었다** 

- **OpenAI**는 내부적으로 PyTorch를 표준화하였지만, 강화 학습 분야에서는 TensorFlow를 활용하고 있다

- Google의 **Google Brain**과 **DeepMind**는 한때 TensorFlow를 주로 사용했으나, 최근에는 연구 가속화를 위해 **JAX**로 전환하고 있다

```python
import tensorflow as tf

# 간단한 선형 회귀 모델
model = tf.keras.Sequential([
    tf.keras.layers.Dense(1, input_shape=(1,))
])

model.compile(optimizer='sgd', loss='mean_squared_error')

# 데이터
x_train = [1, 2, 3, 4]
y_train = [2, 4, 6, 8]

# 모델 훈련
model.fit(x_train, y_train, epochs=10)
```

<br/>

# **Keras**

Keras는 사용하기 쉬운 고수준 딥러닝 API로, 현재 TensorFlow에 통합되었다. 간단하고 직관적인 인터페이스를 통해 빠르게 모델을 프로토타이핑할 수 있어 교육용이나 간단한 모델 구현에 적합하지만 복잡한 모델이나 저수준 제어가 필요한 경우 한계가 있다


<br/>

# **JAX**

JAX는 함수형 프로그래밍과 자동 미분을 결합한 라이브러리로, 기본적으로 함수형 프로그래밍 패러다임을 따르며, XLA를 활용하는데 최적화되어있다. 특히 자동 미분과 XLA 컴파일러를 사용하여 연산을 JIT(Just-In-Time) 방식으로 컴파일하고, 이를 통해 연산 성능을 크게 최적화할 수 있다

또한 여러 GPU 또는 TPU에서 쉽게 자동 병렬화와 분산 학습을 지원한다

- 구글의 **Google Brain**과 **DeepMind**는 한때 TensorFlow를 주로 사용했으나, 최근에는 연구 가속화를 위해 **JAX**로 전환하고 있다. 

```python
import jax
import jax.numpy as jnp
from jax import grad, jit
import optax

# 간단한 선형 회귀 모델
def linear_regression(params, x):
    w, b = params
    return w * x + b

# 손실 함수 (Mean Squared Error)
def loss_fn(params, x, y):
    predictions = linear_regression(params, x)
    return jnp.mean((predictions - y) ** 2)

# 데이터
x_train = jnp.array([[1.0], [2.0], [3.0], [4.0]])
y_train = jnp.array([[2.0], [4.0], [6.0], [8.0]])

# 초기 파라미터 (w, b)
params = [jnp.array([0.0]), jnp.array([0.0])]


optimizer = optax.sgd(learning_rate=0.01)
opt_state = optimizer.init(params)
grad_loss = jax.grad(loss_fn)

# 학습 루프
for epoch in range(10):
    grads = grad_loss(params, x_train, y_train)
    updates, opt_state = optimizer.update(grads, opt_state)
    params = optax.apply_updates(params, updates)
    current_loss = loss_fn(params, x_train, y_train)
```

<br/>

정리하자면, 현재 딥러닝의 연구분야는 PyTorch가, 산업분야는 TensorFlow가 주를 이루며 최근 JAX가 성장하려는 모습을 보인다

[AssemblyAI, "PyTorch vs TensorFlow in 2023"](https://www.assemblyai.com/blog/pytorch-vs-tensorflow-in-2023/), 2023.
[Neel Nanda, "PyTorch Rant"](https://neel04.github.io/my-website/blog/pytorch_rant/), 2023.
