---
title:  "Activation Function"
excerpt: "Activation Function"

categories:
  - Deep Learning 
tags:
  - Deep Learning 
use_math: True 
last_modified_at: 2021-05-17T21:59:00

---

## Activation Function

### Sigmoid function

![sigmoid](./assets/images/sigmoid.png)

생물학적 뉴런이 시그모이드 함수를 구현한 것처럼 보여 초창기 신경망분야에서 이용해 왔지만 최근에는 
일반적으로 ReLU함수가 더 인공신경망에서 잘 작동하는 것으로 밝혀저 ReLU함수를 더 많이 이용합니다.
### step function

![step function](./assets/images/step_function.png)

step function과 sigmoid function은 비선형 함수입니다. 신경망에서는 activation function으로 비선형 함수를 사용해야 합니다. 선형 함수를 사용할 시에는 신경망 층을 깊게 하는
의미가 없어집니다. $f(x) = ax+b$ 라고 하면 $f(f(f(x)))$ 또한 1차 함수를 벗어나지 못하게 됩니다. 그러므로 층을 깊게하는 의미가 없어집니다.

### ReLU function

![ReLU function](./assets/images/relu.png)

연속적이지만 0에서는 미분이 가능하지 않습니다.
경사하강법이 엉뚱한 값으로 튈 수 있지만 실제로는 계산속도도 빠르고 잘 작동합니다.

###softplus

![softplus function](./assets/images/softplus.png)

relu의 변종으로 출력이 항상 양수이어야 할 때 사용

###tanh

![tanh](./assets/images/tanh.png)

어떤 범위 안의 값을 예측하고 싶다면 로지스틱 함수나 하이퍼볼릭 탄젠트 함수를 사용하고 
레이블의 스케일을 조정할 수 있습니다. 로지스틱 함수는 0~1 사이의 값을 반환하고 하이퍼볼릭 탄젠트 함수는 
-1~1 사이의 값을 반환합니다.