---
layout: post
title:  "인프런 리프2기 3. Variable"
subtitle:   "인프런 리프2기"
categories: python
tags: leaf2st
comments: true
---


# 이번에는 자료형에 대해서 깊게 배운다

이번시간에 배울 내용은 매우매우중요하다. 진짜 몇번 강조를 해도 모자라다.

기초자료형은 암기적인 특성이 강하지만, 이걸 암기안하면 나중에 엄청 불편해진다.

그냥 싹다 외우자.

- int, float
- Bool
- String
- List
- Tuple
- Dict
- Set

코딩에서는 `왼쪽` `=` `오른쪽` 일때 왼쪽에 있는 `변수`가 오른쪽에 있는 `내용`을 가진다고 설명했었다. **자료형**이란 `내용`의 **종류**를 구분해주는것을 의미한다.

# 무조건 알아야하는 필수지식

**List** : 순서O,중복O, **수정O, 삭제O**

**Tuple** : 순서O, 중복O, **수정X, 삭제X**

**Dict** : 순서X, 중복애매, **수정O, 삭제O** :: Key중복은 불가, Value중복은 가능

**Set** : 순서X, 중복X

이 키워드와 관련해서는 **mutable,immutable**의 키워드로 구글에 검색해보도록 하자..!

# 헷갈리는 연산종류

```python
// : 몫
% : 나머지
pow(x,y) : x^y
x ** y : x^y
```

# Python vs C언어

파이썬에서는 변수의 자료형을 파이썬프로그램이 직접 할당한다. 이게 무슨말이냐면

```python
A = 3
B = 5.3
C = "hello world"
```

위에 코드처럼 `변수 = 내용` 이런 형식으로 작성을 해주면

- A의 자료형은 int
- B의 자료형은 float
- C의 자료형은 str

라고 파이썬 프로그램이 자동적으로 변수의 자료형을 할당해준다

C언어에서 할당을 어떻게 해주는지 보자

```python
int A = 3;
float B = 5.3;
```

- 변수A의 자료형은 int형
- 변수B의 자료형은 float형

이라는것을 사용자가 직접 명시해주어야한다.

# Casting

바로위에서 Python에서는 파이썬프로그램이 자동으로 자료형을 받는다고했다.

나는 파이썬프로그램이 자동으로 설정한 자료형이 마음에 안들어! 할때 사용할수있는 방법이 'Casting'이다

```python
x = 1
print(type(x))
print(type(float(x)))

```

```python
"""Result"""
<class 'int'>
<class 'float'>
```

- `x=1`에서 x의 자료형은 **int**로 설정되었지만
- `float(x)` 를 통해서 float(x)의 자료형을 **float**로 바꾸어주었다

# Int

Int자료형은 변수가 **정수형**의 내용을 가진다.

```python
X = 10
Y = 20
print("X+Y is ", X+Y)
print("X-Y is ", X-Y)
print("X*Y is ", X*Y)
print("X/Y is ", X/Y)
```

```python
"""Result"""
X+Y is  30
X-Y is  -10
X*Y is  200
X/Y is  0.5
```

그냥 간단한 사칙연산이다. 넘어간다

# Float

float자료형은 변수가 소수형의 내용을 가진다.

```python
X = 1.2
Y = 3.4
print("X+Y is ", X+Y)
print("X-Y is ", X-Y)
print("X*Y is ", X*Y)
print("X/Y is ", X/Y)
```

```python
"""result"""
X+Y is  4.6
X-Y is  -2.2
X*Y is  4.08
X/Y is  0.35294117647058826
```

이것도 간단한 사칙연산이다. 넘어간다.

# String

String대신에 str이라고 보통 약어로 쓰는편이다.

String자료형은 변수가 문자열의 내용을 가진다.

```python
str1 = "Inf"
str2 = "learn"
str3 = "2 st"
str4 = ' '

print(len(str1))
print(len(str2))
print(len(str3))
```

```python
"""result"""
3
5
4
```

`len()` 메소드를 이용해서 자료형의 길이를 알수있다.

```python
str5 = "Oh My \" Goodness"
str6 = "R u \t okay?? \n Sure"
print(str5)
print(str6)

```

```python
"""result"""
Oh My " Goodness
R u      okay??
 Sure
```

`\`이스케이프시퀀스 라고 불리는데 \" 로 작성함으로써, "가 문자열의 내용이다 라는것을 명시한다

`\t` 탭공간만큼 띄우기

`\n` 줄바꿈

# Slicing

Slicing이란 순차적으로 인덱스를 가지는 변수를, 인덱스를 통해서 부분출력하는 기능이다.

string을 예시로 들어본다

```python
str7 = 'hello python'
print(str7[0:4])
print(str7[:len(str7)])
print(str7[1:-2])
```

```python
"""result""
hell
hello python
ello pyth
```

`[0:4]` 0번째인덱스~4-1번째인덱스 까지 출력

`[:len(str7)]` 0번째인덱스~ str7의 길이-1까지의 인덱스까지 출력

`[1:-2]` 1번째인덱스~ 오른쪽끝에서-2번째까지의 인덱스까지 출력

# List

파이썬에서는 배열기능을 제공하고있지않기에, 배열의 역할을 하는 List자료형이 매우중요하다.

List의 기본은 [] 라는것을 꼭 외우자

```python
list1 = []
list2 = list()
list3 = [100,200,'list3']
list4 = [100,200,[101,201]]
```

list1은 []로 **List선언**을 해주었다.

list2는 list()로 ()를 List로 **Casting**해주었다.

list3의 내용에는 **100, 200, 'list3'** 이라는 내용이 있다.

list4의 내용에는 100, 200, **[101,201]의 list**가 있다

```python
a = [10,50,30,40,20]

a.append(5)
print(a)

a.sort()
print(a)

a.reverse()
print(a)

a.insert(1,15)
print(a)
```

```python
"""result"""
[10, 50, 30, 40, 20, 5]
[5, 10, 20, 30, 40, 50]
[50, 40, 30, 20, 10, 5]
[50, 15, 40, 30, 20, 10,
```

`a.append(5)` 5를 a리스트의 마지막에 넣어주고

`a.sort()` a를 오름차순으로 정렬한다

`a.reverse()` a를 반대로 정렬시킨다

`a.insert(1,15)` 인덱스1의 위치에 15라는 값을 넣는다.

# Tuple

List자료형과 매우매우 비슷한 자료형인 Tuple이다.

Tuple은 ()로 작성되고, 수정과 삭제가 안된다.는 점을 유념해두자

```python
tuple1 = ()
tuple2 = (1,)
tuple3 = (10,20,30)
tuple4 = (10,20,'A','B',"C")
tuple5 = (10,20,('A','B',"C"))
```

선언은 list와 비슷하다

tuple4에서는 **10,20,'A','B',"C"** 의 내용을 가지고

tuple5에서는 **10,20, ('A','B',"C")의 tuple** 를 가진다는것만 알아두자

tuple은 수정을 할수없다. 코드로보자

```python
tuple6 = (10,20,30)
tuple6[0] = 1500
print(tuple6)
```

```python
"""reulst"""
Traceback (most recent call last):
  File "c:\Users\kmkimlane\Desktop\pypyfloder\section3.py", line 2, in <module>
    tuple6[0] = 1500
TypeError: 'tuple' object does not support item assignment
```

TypeError 에서 tuple객체는 item assignment(원소 할당)을 지원하지않는다고 나온다.

이점만 빼면 List와 똑같다

# Dictionary

Dictionary자료형은 줄여서 Dict라고도 부른다.

Dict는 {}로 작성되고, 키(key)와 값(value)의 한 쌍으로 움직인다는것을 꼭 명시해두자.

```python
Dicta = {'Who': 'Kim', 
'Phone': '010-1234-5678', 
'Birth': '020410'}

print(Dicta)
```

```python
"""result"""
{'Who': 'Kim', 'Phone': '010-1234-5678', 'Birth': '020410'}
```

Dicta변수의 자료형은 Dict이고

인덱스0 Key : **'Who'**

인덱스0 Value : **'Kim'**

인덱스1 Key : **'Phone'**

인덱스1 Key : **'010-1234-5678'**

인덱스2 Key : **'Birth'**

인덱스2 Value : **'020410'**

이런식으로 Key와 Value가 한쌍으로 존재한다는 점을 주목해야한다.

주요한 특징을 살펴보면

```python
print(Dicta.keys())
print(Dicta.values())
print(Dicta.items())
```

```python
"""result"""

dict_keys(['Who', 'Phone', 'Birth'])
dict_values(['Kim', '010-1234-5678', '020410'])
dict_items([('Who', 'Kim'), ('Phone', '010-1234-5678'), ('Birth', '020410')])
```

`.keys()`와 `.values()`로 Key와 Value를 따로따로 꺼내올수 있다는점

`.items()`를 통해서 Tuple로 구성되어있는 List로 받을수 있다는점

```python
Dicta = {'Who': 'Kim', 
'Phone': '010-1234-5678', 
'Birth': '020410'}

Dicta['Who'] = "Tim"
print(Dicta)
```

```python
"""result"""

{'Who': 'Tim', 'Phone': '010-1234-5678', 'Birth': '020410'}
```

이런식으로 Dicta변수의 Key로 존재하는 `['Who']` 에 = `"Tim"` 이라는 새로운 값을 넣게되면

기존의 **Kim은 없어지고** **Tim**으로 바뀜

# Set

Set는 집합자료형이고 내가 개인적으로 공부했을때는 큰 매력을 못느낀 자료형이다.

간단하게 소개만한다

```python
c = set([1, 2, 3, 5])
d = set([1, 3, 'Pen', 'Pine-Apple', 'Apple'])
```

Set자료형은 기본적으로 List기호`[]` 혹은 Tuple기호`()` 를 사용하지못하고, `set() 키워드`로 직접설정해주어야한다.

```python
d = set([1, 3, 'Pen', 'Pine-Apple', 'Apple'])
t = tuple(d)
l = list(d)

print(type(d))
print(type(t))
print(type(l))
```

```python
"""result"""
<class 'set'>
<class 'tuple'>
<class 'list'>
```

이런식으로 캐스팅해서 사용하기에 좋았다.  

인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!    


