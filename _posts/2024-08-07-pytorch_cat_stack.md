---
title: "[PyTorch] torch.cat vs torch.stack"
date: 2024-07-31 17:30:00 +09:00
categories: [ai, study]
tags:
  [
    pytorch
  ]
math: true
---


**선요약**

| **함수**       | **설명**                                              | **결과 텐서 차원**                  | **사용 사례**                             |
| -------------- | ----------------------------------------------------- | ----------------------------------- | ---------------------------------------- |
| `torch.cat`  | 주어진 차원(axis)을 따라 텐서를 연결                  | 기존 차원의 크기를 증가              | 배치 데이터 결합, 시퀀스 데이터 연결     |
| `torch.stack`| 새로운 차원을 따라 텐서를 쌓음                        | 새로운 차원을 생성하여 차원이 증가   | 미니 배치 생성, 다차원 배열 확장         |

<br/>
<br/>

# **torch.cat(concatenate)**


주어진 텐서 리스트를 지정된 차원(axis)을 따라 연결(concatenate). 이 함수는 기존 차원의 크기를 증가시키지만, 새로운 차원을 생성하지는 않는다


```python
torch.cat(tensors, dim=0)
```

- `tensors`: 결합할 텐서들의 리스트
- `dim`: 텐서를 결합할 차원 (default는 0)

```python
import torch

# 두 개의 텐서를 생성
t1 = torch.tensor([[1, 2], [3, 4]])
print(t1)
# tensor([[1, 2],
#         [3, 4]])

t2 = torch.tensor([[5, 6], [7, 8]])
print(t2)
# tensor([[5, 6],
#         [7, 8]])

result = torch.cat((t1, t2), dim=0)
print(result)
# tensor([[1, 2],
#         [3, 4],
#         [5, 6],
#         [7, 8]])

result = torch.cat((t1, t2), dim=1)
print(result)
# tensor([[1, 2, 5, 6],
#         [3, 4, 7, 8]])
```

<br/>

# **torch.stack**


주어진 텐서 리스트를 새로운 차원(new axis)에 따라 쌓음. 새로운 차원을 생성하여 텐서들을 쌓기 때문에, 결과적으로 텐서의 차원이 증가한다

```python
torch.stack(tensors, dim=0)
```

- `tensors`: 쌓을 텐서들의 리스트
- `dim`: 새로운 차원이 삽입될 위치 (default는 0)

```python
import torch

# 두 개의 텐서를 생성
t1 = torch.tensor([[1, 2], [3, 4]])
print(t1)
# tensor([[1, 2],
#         [3, 4]])

t2 = torch.tensor([[5, 6], [7, 8]])
print(t2)
# tensor([[5, 6],
#         [7, 8]])

result = torch.stack((t1, t2), dim=0)
print(result)
# tensor([[[1, 2],
#          [3, 4]],
#         [[5, 6],
#          [7, 8]]])

result = torch.stack((t1, t2), dim=1)
print(result)
# tensor([[[1, 2],
#          [5, 6]],
#         [[3, 4],
#          [7, 8]]])
```
