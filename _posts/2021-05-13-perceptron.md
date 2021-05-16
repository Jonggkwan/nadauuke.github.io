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

### 1. AND gate
AND 게이트를 퍼셉트론으로 표현하기 위한 $ w_1 w_2 \theta $ 는 무수히 많습니다. 
0.5, 0.5, 0.8 이나 1, 1, 1 일 때 모두 만족합니다.

이를 python으로 구현하면

```python
def AND(x1, x2):
    w1, w2, theta = 0.5, 0.5, 0.5
    if x1*w1 + x2*w2 <= theta:
        return 0
    else:
        return 1
```
### 2. NAND gate
NAND gate는 AND gate 매개변수들을 모두 반전하면 됩니다.

```python
def NAND(x1, x2):
    w1, w2, theta = -0.5, -0.5, -0.5
    if x1*w1 + x2*w2 <= theta:
        return 0
    else:
        return 1
```
### 3. OR gate
OR gate도 변수를 적당히 조절 하면 구현 가능합니다.
```python
def OR(x1, x2):
    w1, w2, theta = 0.5, 0.5, 0.3
    if x1*w1 + x2*w2 <= theta:
        return 0
    else:
        return 1
```

$ y=\left\lbrace\begin{matrix}\ 0 \ (w_1x_1\ +\ w_2x_2\ +\ b\ \leq\  \theta ) \\\ 1 \ (w_1x_1\ +\ w_2x_2\ +\ b\ > \  \theta )\end{matrix}\right. $
에서 b를 편향(bias)라고 합니다.

bias를 적용시켜 AND gate를 구현해 보면

```python
def AND(x1, x2):
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.7
    if np.sum(w*x + b) <= 0:
        return 0
    else:
        return 1
```
### 4. XOR gate
Perceptron을 이용해 XOR을 구현하려면 위의 게이트를 조합해야 합니다.

$y\ =\ (x_1 \barwedge  x_2 ) \wedge (x_1\vee x_2)$
∧ 는 AND ⊼ 는 NAND ∨는 or 입니다.

```python
def XOR(x1, x2):
    s1 = NAND(x1, x2)
    s2 = OR(x1, x2)
    y = AND(s1, s2)
    return y
```
이와 같이 층이 여러개인 퍼셉트론을 다층 퍼셉트론(multi-layer perceptron)이라 합니다.
문헌에 따라 입력층을 포함하여 3층 퍼셉트론이라 부를 수도 있고 포함하지 않고 2층 퍼셉트론이라 부르기도 합니다.
