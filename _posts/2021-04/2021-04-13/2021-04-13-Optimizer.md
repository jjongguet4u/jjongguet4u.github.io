---
layout: post
title:  "OPTIMIZER족보"
subtitle:   "ML기미상궁"
categories: ml
tags: machinelearning
comments: true
---


# ML문제3대장

### 1. Underfitting
  
<img src="/assets/img/202104/0413/1.jpg">  

Gradient Vanishing : 딥러닝에서 Layer단이 깊을수록 기울기 업데이트가 적게되는 현상

→ activation func로 sigmoid대신에 Relu를 사용함

⇒ 기울기 전달 부분에서 문제해결

### 2. Overfitting

<img src="/assets/img/202104/0413/2.jpg">

DropOut : Train과정에서 의도적으로 정보를 누락or일부노드를 꺼서 

→ 학습에 유연성을 제공

### 3. Slow (학습시간)

Batch ?

Learning Rate ?

Acc ?

→ 이와 관련된것이 OPTIMIZER

⇒ 종류와 특징들에 대해서 정리

# OPTIMIZER족보

<img src="/assets/img/202104/0413/3.jpg">  
<img src="/assets/img/202104/0413/4.jpg">

### 속도와 속력의 느낌st

속도 : Vector (⇒ 방향에 초점을 둠)

속력 : Scala (⇒ 값에 초점을 둠)

Step사이즈에 신경 → 제곱값

# MSE, MAE, L1, L2

MAE는 실제값과 error값의 차이를 |절댓값| 으로 바꿔서 사용함

→ 에러의 크기가 그대로 반영됨

MSE는 실제값과 예측값의 차이를 ^2해서 사용함

→ 면적의 합으로 사용함  

<img src="/assets/img/202104/0413/5.jpg">  
<img src="/assets/img/202104/0413/6.jpg">

→ 최적값을 구하기엔 MSE가 좋지만, MAE가 Outliar를 좀더 잘 조절하수있음

### L1 Regularization

<img src="/assets/img/202104/0413/7.jpg">  

### L2 Regularization  

<img src="/assets/img/202104/0413/8.jpg">

L1는 경우에 따라 특정 feature가 없어도 동일한 값을 낼수가 있음 

L2는 각각의 벡터에 대해 항상 최적의 값을 도출해냄

→ L1은 feature selection이 가능하다는점

⇒ L1은 sparse modeling에 적합함

<img src="/assets/img/202104/0413/9.jpg">  

→ 그러나 L1의 경우, 그림처럼 '미분불가능'한 지점이 존재하는것이 특징이다.

# GD vs SGD


<img src="/assets/img/202104/0413/10.jpg">  


GD : Gradient Descent

- Full-batch(전체데이터를 기반으로) → 최적화된 1step

SGD : Stochastic Gradient Descent

- mini-batch(일부데이터를 기반으로) → 일단 1step
- GD에 비해서 빈도수가 잦음
- 1step에서 사용하는 Data의 크기 자체가 작음 → 메모리 사용량 적음 → 학습속도 빠름
- 1step을 진행해도, 최적화된 1step이 아님

# Momentum

SGD + 관성의 개념 ⇒ Momentum

이전step의 '방향'을 참고하여, 같은 방향으로 일정한 비율만 수정되게 하는 방법

+-+-+-+- ⇒ ++--++-- 

상대적으로 적게 지그재그한다...!
<img src="/assets/img/202104/0413/11.jpg">  

<img src="/assets/img/202104/0413/12.jpg">  

현재 Parameter위치에서 현재Gradient를 계산 → ∇θtJ(θt)

현재의 Moment Vt를 구해서 → vt=γvt−1+η∇θtJ(θt)

⇒ **실제 Momentum = 현재의 Moment + 현재의 Gradient**

# NAG : Nesterov Accelrated Gradient

Momentum + 현재 시점에서 다음이동방향예측 ⇒ NAG

다음에 학습할 데이터가 누가봐도 학습에 악영향을 줄거같은상황

→ 굳이 100% original로 사용할 필요가없다?

⇒ 판단하에 Actual Step이 감소할수 있음

<img src="/assets/img/202104/0413/13.jpg">  

<img src="/assets/img/202104/0413/14.jpg">  


현재의 Parameter위치에서 Momentum을 계산함

Momentum이 적용된 시점인 다음시점에서, Gradient를 계산함 η∇θtJ(θt−γvt−1)
→(현재 수식에서는 t일때와 t-1일때로 표현되었음)

**⇒ 실제 Momentum = 현재의Momentum + 다음의 Gradient**

*lookahead Optimizer

로컬 minimum을 벗어나기 어려울때 사용하면 좋은 성능을 보여주는 기법

기존 optimizer를 사용하여 k번 Gradient descent진행 → 첫번째 파라미터의 방향으로 돌아가는 기법

# Adagrad : Adaptive Gradient

train을 어느정도 돌렸는데

1. 많이 변화하지 않은 parameter

    → 이미 어느정도 수렴했겠다. 라는 판단 하에 step size를 작게 설정함

    ⇒ 조금 더 세밀하고, 정확하게 탐색

2. 많이 변화했던 parameter

    → 아직 수렴하려면 멀었겠다. 라는 판단 하에 step size를 크게 설정함

    ⇒ 조금 더 큰값으로, 정확하지 않아도 급하게 탐색

Adagrad는 얼마나 업데이트 되었는지에 대한 정보가 필요하므로 이전 gradient를 저장함

<img src="/assets/img/202104/0413/15.jpg">  

G : 현재의 gradient

G(t) = G(t-1) + (t에서의 gradient )^2

⇒ 모든 Gradient에 대한 sum of square

- MAE의 기법을 적용해서 표현할수 있었음

문제점 

Iteration이 계속될수록 G가 계속증가해서 step size가 너무 작아질수도 있음

# RMSprop : 
지수 이동 평균(exponential moving average)

Adagrad에서 G(t)가 무한히 커지는 것을 방지하는 방법

최근값과 이전값에 각각 다른 가중치를 둠 → 최근값을 좀 더 많이 반영하기 위함

<img src="/assets/img/202104/0413/16.jpg">  

<img src="/assets/img/202104/0413/17.jpg">  


1주기가 지날때마다 (1-a)라는 가중치가 이전값에 곱해지는데, 

(1-a)가 1보다 작기때문에 영향력이 지속적으로 줄어듬

<img src="/assets/img/202104/0413/18.jpg">

Adagrad에서는 G(t)를 구성하는 항이 그냥 더해지지만, 

RMS에서는 지수평균으로 더해진다

# Adam : Adaptive Momentum Estimation

RMSprop + Momentum의 결합

알고리즘의 구성 : Momentum을 계산하는부분 + Bias를 보정하는 부분

<img src="/assets/img/202104/0413/19.jpg">

<img src="/assets/img/202104/0413/20.jpg">

gt : t일때의 Gradient

mt : t일때 gradient의 1st momentum

→ Gradient값을 좀 더 빠르게 계산할수록 돕는 역할

vt : t일때 gradient의 2nd momentum

→ 데이터의 분포가 Sparse한 곳에서, 빠르게 Sparse한 영역을 벗어나도록 돕는 역할

m^t와 v^t로 처리하여서 사용함

⇒ 스텝사이즈와 스텝방향의 개념이 동시에 적용된 것이 특징이라고 판단하면 될것같다

Bias 편향문제

m0, v0의 값이 초기에 0으로 Initialize되는데

이동평균을 구하면 0으로 편향된 값이 나올것임

그래서 mt^와 vt^에서 1-b^t 값을 나누어서 바이어스 보정을 해줌

b1=0.9, b2=0.999로 설정해줬었다고 함

(이 값에 대해서는 수학적으로 엄청 깊게 들어가는듯 하다)

# NADAM : ADAM - Momentum + NAG

NADAM의 방식

현재Paramter위치에서 → Gradient와 Momentum값을 구하는것(Momentum)아닌

Momentum값으로 먼저 이동하고 → Gradient를 구하는것(NAG)

# RADAM : Rectified ADAM

ADAM의 한계점

학습 초기에 Local optima에 일찍 도달하는현상이 존재했음

→ warmup을 통해서 해결

WARMUP

학습 초반부에 사용하는 방법

설정한 Learning rate를 선형적으로 조금씩 증가함
→ learning rate를 변화시켜주는 방법

⇒ Local minimum에 빠지는것을 방지한다고 함

# ADAMW

ADAM vs SGD

L2 Regularization과 Weight decay 관점에서 ADAM의 일반화성능이 
SGD보다 낮음

[...딥하게 파야하는데, 생각보다 깊게 봐야할것 같아서 보류...]

# Reference

ML

[https://www.slideshare.net/yongho/ss-79607172](https://www.slideshare.net/yongho/ss-79607172)

OPTIMIZER

1. [https://hiddenbeginner.github.io/deeplearning/2019/09/22/optimization_algorithms_in_deep_learning.html#momentum](https://hiddenbeginner.github.io/deeplearning/2019/09/22/optimization_algorithms_in_deep_learning.html#momentum)
2. [https://twinw.tistory.com/247](https://twinw.tistory.com/247)
3. [https://mole-starseeker.tistory.com/48](https://mole-starseeker.tistory.com/48)

MSE MAE L1 L2

[https://bo-10000.tistory.com/44](https://bo-10000.tistory.com/44)

[https://mizykk.tistory.com/102](https://mizykk.tistory.com/102)

[https://light-tree.tistory.com/125](https://light-tree.tistory.com/125)

NADAM

[https://tgd.kr/c/deeplearning/19860071](https://tgd.kr/c/deeplearning/19860071)

RADAM

[https://choice-life.tistory.com/34](https://choice-life.tistory.com/34)