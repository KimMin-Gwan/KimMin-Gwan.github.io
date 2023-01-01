---
title:  "#2 - 활성함수" 
excerpt: "텐서플로우 기초"

categories:
  -  AI
tags:
  - [AI, 기계학습, 딥러닝]

last_modified_at: 2023-01-01
---

## 활성함수(Activation Function)
- 활성함수는 각 노드에서 연산된 값을 압축하여 다음 레이어로 얼마나 보낼지 결정하게 해준다.
- 각 Layer에 연산 결과를 다음 Layer로 출력하기 위해서 비선형적 형태의 함수를 사용하여 다음 레이어로 전달한다.
- 활성함수를 사용하지 않은 상태에서는 선형적인 예측만 가능하게 되지만 활성함수를 사용하게 되면 비 선형적인 예측도 가능하게 해준다.
- 다음 레이어로 신호를 얼마나 전달할지 결정하는 특징 때문에 종종 전달함수(transfer function)라고도 불린다.
- 마지막 노드(Output Layer)에서는 활성함수를 사용하지 않아도 된다.

<br>

![need_of_activation_function](https://user-images.githubusercontent.com/105574034/210176153-fed907d0-d6e8-4bf3-b198-3fd476c90ac6.jpg)


- 위 사진처럼 활성함수가 없으면 Hidden Layer는 아무의미 없어지며, Hidden Layer가 없다면 딥러닝이라고 하기 어렵다.
- 활성함수를 사용하면 더 많은 Hidden Layer를 쌓을 수 있고, 더 복잡한 예측이 가능하게 된다.

<br>

## 주요 활성함수

+ Step Function
    + 0을 기준으로 0보다 작으면 데이터를 보내지 않고, 0보다 크거나 같으면 데이터를 보낸다.
    + 실제로 사용할 일은 잘 없다.

<br>

+ Sigmoid Function

    ![sigmoid](https://user-images.githubusercontent.com/105574034/210175563-cd607f74-92df-42c4-bb51-373a248a63e5.PNG)

    ![sigmoid_graph](https://user-images.githubusercontent.com/105574034/210175575-6f7359a7-2f05-4be7-ad2d-4d221e5357c0.PNG)

    + 입력이 0일때 0.5가 출력되고 값이 작아질수록 0, 값이 커질수록 1에 가까워진다.
    + 0부터 1사이의 값이 출력되어야 한다면 사용을 고려하자.
    + 최근에는 기울기 소멸 문제(Vanishing Gradient problem) 문제 때문에 사용이 꺼려지는 추세라고 한다.
        + 미분된 Sigmoid Function을 살펴보면 입력이 크면 클수록 0에 가까워 지는 것을 알 수 있다.
        + x가 커지면 다음 Layer로 출력이 전달 되어야 하는데, 기울기가 0인 상태가 반복되면 가중치가 변하기 어렵다.
        + [기울기 소멸 문제 - 위키백과](https://ko.wikipedia.org/wiki/%EA%B8%B0%EC%9A%B8%EA%B8%B0_%EC%86%8C%EB%A9%B8_%EB%AC%B8%EC%A0%9C)

<br>

+ Hyperbolic Tangent

    ![tanh](https://user-images.githubusercontent.com/105574034/210175589-1306613d-9217-4c38-82ad-cb39a3f123c9.PNG)

    ![tanh_graph](https://user-images.githubusercontent.com/105574034/210175594-654b83e4-cb5f-404e-97aa-6f73e66f4ab2.PNG)

    + 입력이 0일때 0이 출력되고, 값이 작아질수록 1, 값이 작아질수록 -1에 가까워진다.
    + Sigmoid Function과 유사하지만, 값이 더 급격하게 변화함
    + Sigmoid Fucntion과 동일하게 기울기 소멸 문제가 있음

<br>

+ Rectified Linear Unit(ReLU)

    ![ReLU](https://user-images.githubusercontent.com/105574034/210175624-50ae05b9-41d4-4966-a230-54ce366bac6c.PNG)

    ![ReLU_Graph](https://user-images.githubusercontent.com/105574034/210175625-ab02303d-a32c-4773-a122-fe8f94808ff4.PNG)

    + 입력이 0보다 작으면 출력이 0, 입력이 0보다 크면 기울기가 1인 에 따라 출력이 나온다.
    + 학습시간이 상대적으로 빠르고, 연산 비용이나 구현이 유리하다.
    + 0보다 작은 입력에 대하여 기울기가 0인 출력이 나오기 때문에 해당 노드가 사용되지 않을 가능성이 있다.
    + 입력이 커져도 미분값이 0으로 수렴하지 않기 때문에 가장 자주 쓰인다.

<br>

+ Leaky Rectifide Linear Unit (Leaky ReLU) 

    ![Leaky_ReLU](https://user-images.githubusercontent.com/105574034/210175639-08925bbd-b394-48b0-9393-a3eb195c3994.PNG)

    ![Leaky_ReLU_Graph](https://user-images.githubusercontent.com/105574034/210175641-360c7c6b-c3ee-4f89-8065-75c0ddc47011.PNG)

    + 일반적인 ReLU에서 0보다 작은 입력값에 대한 기울기 문제를 해결한 활성함수이다.
    + 보통 ReLU를 먼저 사용해보고, 문제가 있다면 차선책으로 Leaky ReLU를 사용한다.

<br>

+ 이 외에도 다양한 활성함수가 있다.
    + SoftMax : 입력이 여러개일 때의 Sigamoid Function을 일반화한 함수
    + ELU, SeLU : ReLU함수에서 0보다 작은 입력 부분을 부드럽게 만들었다.
    + PReLU : ReLU함수에서 0보다 작은 입력에서 발생하는 편향을 제거하기 위해 고안된
    + Softplus : ReLU함수를 부드럽게 만들었다. 미분하면 Sigmoid Function이 된다.
    + Softsign : Hyperbolid Tangent 함수를 개선한 형태이다.
    + Swish : 구글이 고안한 ReLU를 대체할 활성함수이다. 깊은 레이어를 학습할때 더 높은 효과를 보인다.
    + [종류별로정리된글](https://yeomko.tistory.com/39)

<br>

- 다음글에서는 적절한 가중치를 찾아내는 방법에 대하여 알아보겠습니다.


<br>

    😺 오타나 논리적 오류 지적은 언제든지 환영합니다!😺   
    항상 읽어주셔서 감사합니다~ 🙏