---
layout: post
title:  "인프런 리프2기 6.Class, Instance, Module, Package"
subtitle:   "인프런 리프2기"
categories: out
tags: leaf2st
comments: true
---

# Class vs Object

Class와 Object의 관계는 마치 **빵틀과** **빵의 관계**라고 생각하면 쉽다

- **Class** : 똑같은것을 계속해서 만들수 있는 틀.찍어내기만하면됨 (**빵틀**)
- **Object** : Class에 의해서 만들어진 내용. (**빵**)

# Class

기본형식

```python
class 클래스명 :
	클래스속성
	def 클래스함수(self,인자1,인자2...):
		함수내용1
		함수내용2
```

- 이때 중요한점은 **클래스함수의 인자로 (self)**를 하나 써준다는것이다.
- **self를 쓰면 객체의 매개변수**로 들어간다.

예제를 들어보자

```python
class Man :
	def __init__(self,name, age):
		self.name = name
		self.age = age

A = Man("Inflearn",13)
B = Man("leaf2st",15)

print(A.name, A.age)
print(B.name, B.age)
```

```python
"""result"""
Inflearn 13
leaf2st 15
```

`A = Man("Inflearn",13)
B = Man("leaf2st",15)`

이 부분에서 `A,B`는 **Man의 클래스**를 가지는 **객체**가되는것이다.

클래스의 메소드인 `__init__`을 통해서`A,B`가`name,age`를 사용할수 있게되는것이라고 생각해야한다

```python
print(A==B)
print(id(A))
print(id(B))
```

```python
"""result"""
False
2591699657968
2591699867872
```

A와 B는 같은 기능을 사용할수 있지만, **같은 내용은 아니다**

A=Man()과 B=Man()에서 **서로 다른 A객체와 B객체가** 생기는것이고, 이는 `id(A)`, `id(B)`에서도 확인할수 있다

# Instance

**Class**는 일종의 **빵틀**이라고 생각했었다. 그렇기에 위의 예제에서 A와 B는 **공통된 내용에 접근하지 못했다.** 이번엔 Instance를 사용해보자

```python
class BOX:
	stock_number=0
	
	def __init__(self,name):
		self.name = name
		BOX.stock_number +=1
	
	def __del(self):
		BOX.stock_number -=1

user1 = BOX("JJONG")
user2 = BOX("GEUT")

print(BOX.stock_number)
print(user1.name)
print(user2.name)
```

```python
"""result"""
2
JJONG
GEUT
```

**user1와 user2**가 **선언**되는 부분에서, **BOX는 호출되고** 공통된 변수인 BOX.stock_number에 **접근**하여

**+1+1** 이 되어 `print(BOX.stock_number)`에서 2가 나온다

# 상속

상속이란 덮어씌우는 과정을 의미한다. 위에서 사용했던 Box를 예제로 사용한다

```python
class BOX:
	stock_number=0
	
	def __init__(self,name):
		self.name = name
		BOX.stock_number +=1
	
	def __del(self):
		BOX.stock_number -=1

class BOX:
	def __init__(self,name, demand):
		self.name = name
		self.demand = demand

	def speak(self,sound):
		return "{} says {} ".format(self.name, sound)

user3 = BOX('INFLEARN',4)
print(user3.name)
print(user3.demand)
print(user3.speak('MUYAHO'))
```

```python
"""result"""
INFLEARN
4
INFLEARN says MUYAHO
```

이런식으로 맨위에 BOX가 있어도, 하단에 동일한 이름을 가진 BOX가 다른 내용을 가진다면

다른내용을 통해서 접근가능하다

# Module

Module은 일종의 묶음이다. 함수, 변수, 클래스 등 여러가지 구성요소를 묶어서 한번에 사용할수 있게 한다

계산기 예제를 가져와봤다

```python
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x , y):
    return x / y
    
def power(x, y):
    return x ** y
```

이런 코드를 하나의 파일에서 놔두고

**다른 파일에서 import해서 사용하는것이다**

# Package

**패키지는 모듈을 디렉토리 형식으로 구조화한것이다.** 

패키지 내부에서는 무조건`__init**__**`이라는 파일이 반드시 하나 존재해야한다.

예를들어 

```python
Study/
    __init__.py
    MachineLearning/
        __init__.py
        Regression.py
        Classification.py

    RecommendSystem/
        __init__.py
        ContentBased.py
        CollaborativeFilltering.py

    ReinforceLearning/
        __init__.py
        DQN.py
        DDPG.py
```

- Study package는`__init__`을 가지고있다
- Study내부의 MachineLearning, RecommendSystedm, ReinforcementLearning디렉터리는 모두 확장자가 .py인 모듈이다. init을 하나씩 가지고 있다는것이 특징이다.

다른 .py파일에서 해당 패키지를 사용할때는 다음처럼 명시한다.

```python
import Study.MachineLearning.*
import Study.RecommendSystem.ContentBased
import Study.RecommendSystem.CollaborativeFilltering
import Study.ReinforceLearning.*
```

- MachineLearning디렉토리에 있는 **모든** .py(Regression,Classification)가 불러와지고
- RecommendSystem디렉토리에 있는 ContentBased,CollaborativeFilltering이 불러와지고
- ReinforceLearning디렉토리에 있는 **모든** .py(DQN,DDPG)가 불러와진다
  
인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!    


