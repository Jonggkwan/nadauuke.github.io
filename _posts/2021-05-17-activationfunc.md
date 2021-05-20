---
title:  "Activation Function"

categories:
  - Deep Learning 
tags:
  - Deep Learning 
use_math: True 

---

## Activation Function

### Sigmoid function

![sigmoid](/assets/images/sigmoid.png)

생물학적 뉴런이 시그모이드 함수를 구현한 것처럼 보여 초창기 신경망분야에서 이용해 왔지만 최근에는 
일반적으로 ReLU함수가 더 인공신경망에서 잘 작동하는 것으로 밝혀저 ReLU함수를 더 많이 이용합니다.
### step function

![step function](/assets/images/step_function.png)

step function과 sigmoid function은 비선형 함수입니다. 신경망에서는 activation function으로 비선형 함수를 사용해야 합니다. 선형 함수를 사용할 시에는 신경망 층을 깊게 하는
의미가 없어집니다. $f(x) = ax+b$ 라고 하면 $f(f(f(x)))$ 또한 1차 함수를 벗어나지 못하게 됩니다. 그러므로 층을 깊게하는 의미가 없어집니다.

### ReLU function

![ReLU function](/assets/images/relu.png)

연속적이지만 0에서는 미분이 가능하지 않습니다.
경사하강법이 엉뚱한 값으로 튈 수 있지만 실제로는 계산속도도 빠르고 잘 작동합니다.

### softplus

![softplus function](/assets/images/softplus.png)

relu의 변종으로 출력이 항상 양수이어야 할 때 사용

### tanh

![tanh](/assets/images/tanh.png)

어떤 범위 안의 값을 예측하고 싶다면 로지스틱 함수나 하이퍼볼릭 탄젠트 함수를 사용하고 
레이블의 스케일을 조정할 수 있습니다. 로지스틱 함수는 0 ~ 1 사이의 값을 반환하고 하이퍼볼릭 탄젠트 함수는 
-1 ~ 1 사이의 값을 반환합니다.

### softmax

다중 분류시 한 클래스에만 속할 수 있다면 클래스마다 하나의 출력이 필요합니다.
softmax 함수는 모든 예측 확률을 0과 1사이로 만들고 더했을 때 1이 되도록합니다
(클래스가 서로 배타적일 경우). 이를 다중 분류(multiclass classification)라 합니다.
확률 분포를 예측해야 하므로 손실함수에는 일반적으로 cross entrophy loss (log loss)을 선택하는 것이 좋습니다.

$ p\hat{}_k = \sigma(s(x))_k = \frac{exp(s_k(x))}{\sum^k_{j=1}exp(s_j(x))}$
K는 클래스 수입니다.
$s(x)$는 입력 x에 대한 각 클래스의 확률을 출력하는 함수 입니다.
$\simga (s(x))_k $ 는 입력 x에 대한 각 클래스의 점수가 주어졌을 때 이 샘플이 클래스 K에 속활 확률 입니다.
