---
title: "[쇼츠논문리뷰] Perceiver/PerceiverIO"
date: 2024-05-05 21:20:59 +09:00
categories: [ai, paper review]
tags:
  [
    ai,
    ai paper,
    ai paper review,
    perceiver,
    perceiver io,
    shorts review
  ]
---

**선요약**

`Perceiver` : 다양한 type의 input data들을 latent space와 cross attention을 이용해 처리하는 모델 구조

`Perceiver IO` : classification에 특화되어 있는 Perceiver을 다양한 output 처리가 가능하게 확장

`Contribution` : task-specific 아키텍쳐 없이도 모든 task에 대해 이용 가능한 단일 generality 모델 제안

<br/>
<br/>


# **Perceiver**

![perceiver](/assets/img/paper/perceiver/perceiver1.png){: width="70%" height="70%"}


1. input data의 byte array를 latent array와 cross attetion시켜 latent space로 데이터를 압축
2. latent array의 self attetion 진행
3. 이를 반복하여 transformer tower구축
4. complexity가 linear complexity가 되어 다양한 type의 input에도 큰 계산량 없이 처리가능
<br/>

# **Perceiver IO**

![perceiverio](/assets/img/paper/perceiver/perceiverio1.png){: width="70%" height="70%"}

Perceiver모델에 output quert array를 추가하여 여러 task에 대한 decoding part추가