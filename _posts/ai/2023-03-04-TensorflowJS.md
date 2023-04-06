---
title:  "#7 - Tensorflow JS 사용" 
excerpt: "텐서플로우 기초"

categories:
  -  AI
tags:
  - [AI, 기계학습, 딥러닝]

last_modified_at: 2023-03-04
---


## 순서가 중요한 학습
 - 언어나 음성 데이터는 순서가 학습에 중요한 파라미터가 된다.
 - 단위 데이터를 순차적으로 연산하는 방법으로 학습이 필요하다.
 - 이 과정에서 앞선 연산 결과가 다음 연산 결과에 영향을 주어야만 한다.

## Recurrent Neural Network(RNN)
 - 순환 신경망이라고도 한다.
 - RNN에서는 출력층으로만 연산 결과가 모두 전달되는 것이 아닌, 다음 연산의 입력으로도 일부가 전달된다.
 - Simple RNN에서는 출력층에서 hidden state를 통해 다음 연산에 동작하는 노드로 연산결과의 일부를 전달한다.
 - 다음 연산에서는 hidden state를 고려한 연산을 하여 순서에 따른 학습이 가능하게 된다.

## Diminishing Gradient



## LSTM

## GRU

## Sequence & Vector

## KoNLPy


## 결론
 - Convolutional Layer를 사용하여 이미지를 분석하는데 사용하자
 - Convolutional Layer는 kernel를 통해 feature extraction 하게 한다.
 - Convolutional Layerd와 Pooling Layer를 함께 사용하면 translation invariance 의 장점을 가진다.
 + 일반적인 CNN구성법
    1. Image Input
    2. Filters
    3. Convolution Layers
    4. Pooling
    5. Flattening
    6. Output
 

 - 다음 포스트에서는 실제로 Tensorflow를 사용하여 학습해보겠습니다.


<br>

    😺 오타나 논리적 오류 지적은 언제든지 환영합니다!😺   
    항상 읽어주셔서 감사합니다~ 🙏