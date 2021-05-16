---
title:  "파이썬으로 퍼셉트론 구현"
excerpt: "파이썬으로 퍼셉트론 구현"

categories:
  - Deep Learning
tags:
  - Deep Learning
use_math: True
last_modified_at: 2021-05-12T21:59:00
---


### 퍼셉트론이란



퍼셉트론이란 다수의 신호를 입력받아 하나의 신호를 출력합니다.


$ y=\left\lbrace\begin{matrix}\ 0 \ (w_1x_1\ +\ w_2x_2\ \leq\  \theta ) \\\ 1 \ (w_1x_1\ +\ w_2x_2\ > \  \theta )\end{matrix}\right. $


w는 가중치를 뜻하고 x는 입력신호를 뜻합니다.
하나의 퍼셉트론으로는  직선 하나만 표현이 가능합니다.

## 1. AND gate
AND 게이트를 퍼셉트론으로 표현하기 위한 $ w_1 w_2 \theta $ 는 무수히 많습니다. 
0.5, 0.5, 0.8 이나 1, 1, 1 일 때 모두 만족합니다.

이를 python으로 구현하면

```python
def AND(x1, x2):
    w1, w2. theta = 0.5, 0.5, 0.5
    if x1*w1 + x2*w2 <= theta:
        return 0
    else:
        return 1
```


그러므로 multi-layer-perceptron으로 XOR 문제 등을 풀 수 있습니다.



