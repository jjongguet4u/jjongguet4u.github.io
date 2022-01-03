---
layout: post
title:  "인프런 리프2기 5.Def, *args, **kwargs"
subtitle:   "인프런 리프2기"
categories: out
tags: leaf2st
comments: true
---
  
# 함수는 왜 정의하는가?
내가 원하는 소스코드를 입맛대로 묶어놓을수 있기 때문이다. 차근차근히 보자

# Def문

Def 키워드는 함수를 정의할때 쓰는거다

주요 형식은 이렇다

```python
def 함수이름(변수1, 변수2, 변수3 ...):
	내용1
	내용2
	내용3 
	...

```

단, 주의할점은 **def** 함수이름(변수1, 변수2, 변수3 ...): 이 끝난 이후 **줄바꿈을 하고**,

**탭(띄어쓰기4칸)** 을 **꼭** 해야한다는것이다. 이건 Python에서 정해놓은거다

예제로 보자

```python
def hello_func(a1):
    print("Hello", a1)

hello_func("apple")
```

```python
"""result"""
Hello apple
```

이때 `def hello_func(a1):`  부분을 **함수의 정의**라고 부르고

`hello_func("apple")` 부분을 **함수의 호출**이라고 한다

이번에는 return이라는 키워드가 나온다

return은 **"이 함수가 끝났을때 무슨값을 밖으로 내보내겠습니다"** 라는 의미이다.

다른예제를보자

```python
def addmul_func(input1):
	y1 = input1 + 10
	y2 = input1 * 2
	return y1, y2

y1, y2 = addmul_func(15)
print(y1,y2)
```

```python
"""result"""
25 30
```

**def** 내부에 있는 **y1과 y2는 꼭 같을 필요는없다.**

**def**내부에 있는 **y1,y2는 def내부에서만 정의된다**

```python
def addmul_func(input1):
	A = input1 + 10
	B = input1 * 2
	return A, B

y1, y2 = addmul_func(15)
print(y1,y2)
```

def문 내부에서 `y1`과 `y2`를 `A`와 `B`로 바꿔보았다. 두 함수는 동일한 기능을 가진다.

인자가 여러개일때도 사용가능하다

```python
def addmul_func(A,B):
	result1 = A + 10
	result2 = B * 2
	return result1, result2

X=2
Y=4
number1, number2 = addmul_func(X,Y)
print(number1, number2)
```

```python
"""result"""
12 8
```

반환하는 자료형은 숫자 이외에도 많다

```python
def tuple_func(x):
	y1 = x+5
	y2 = x+15
	y3 = x+25
	return (y1,y2,y3)

def list_func(x):
	y1 = x+5
	y2 = x+15
	y3 = x+25
	return [y1,y2,y3]

def dict_func(x):
	y1 = x+5
	y2 = x+15
	y3 = x+25
	return {'number1': y1, 'number2':y2, 'number3':y3}

x=5
print('{}'.format(tuple_func(x)))
print('{}'.format(list_func(x)))
print('{}'.format(dict_func(x)))
```

```python
"""result""
(10, 20, 30)
[10, 20, 30]
{'number1': 10, 'number2': 20, 'number3': 30}
```

이런식으로 **반환하는 자료형**을 **return**부분에서 **명시**해줄수있다

# ***args**

- ***args**는 ***arguments의 줄임말**이다. **줄임말일뿐 꼭 저 단어를 사용할 필요는없다**
- ***args**는 **여러개의 매개변수**를 함수의 인수로 받고싶을때 사용하는 키워드다
- ***args**에서 중요한건 결과값의 **형태와, 순서**이다.

형식

```python
def 함수이름(인자1, 인자2, 인자3 ... *args):
	내용1(args)
```

- 인자로 `*args`를 받지만, 함수내부에서는 `args`를 사용한다

```python
def name(*args):
    print(args)
```

```python
***result***
('hello', 'inflearn', 'leaf', '2st')
```

- 결과가 **()Tuple**의 형태로 나온다는것에 주목해야한다

***args** 키워드는 함수의 인자위치에서 **여러개의 매개변수**를 **함수의 인수**로 받는다고 하였다

그래서 생기는 문제중 하나는, **다른 변수들과 섞여있을때**이다.

```python
def name1(nickname, *args):
    print(nickname, args)

name1("NICKNAME", "hello","inflearn","leaf","2st")
```

```python
***result***
NICKNAME ('hello', 'inflearn', 'leaf', '2st')
```

- 함수의 인자부분에서 : 일반변수nickname가 앞에 나온경우

여기서 주목해야할점은 nickname으로 지정된 NICKNAME은 앞으로나오고, ***arg**는 따로 **튜플로** 만들어졌다는것이다.

여기서 *args와 nickname의 위치를 바꿔보자

```python
def name1(*args, nickname):
    print(nickname, args)

name1("NICKNAME", "hello","inflearn","leaf","2st")
```

```python
Traceback (most recent call last):
  File "c:\Users\kmkimlane\Desktop\pypyfloder\section4.py", line 4, in <module>
    name1("NICKNAME", "hello","inflearn","leaf","2st")
TypeError: name1() missing 1 required keyword-only argument: 'nickname'
```

- 함수의 인자부분에서 : ***args가 앞에나온경**우
- 오류가 나오는이유

`*args`는 **불특정다수개**를 한꺼번에 받는다. 이때 불특정다수개의 갯수는 주어지지않았기때문에,

**함수의 호출**부분에서 NICKNAME부터 2st 중에, **어디까지 받아야하는지 모르는 상황이 발생**하여 에러가 발생한것이다.

# **kwargs

- `**kwargs`는 keyword argument의 줄임말로, **키워드를 제공한다**
- `**kwargs`는 **키워드—특정값의 형태**로 함수를 호출할수 있다

형식 

```python
def 함수이름(**kwargs):
	내용(kwargs)
```

예제

```python
def hellopy(**kwargs):
	print(kwargs)

hellopy(first="inflearn", second="leaf", thrid="2st")
```

```python
"""result"""
{'first': 'inflearn', 'second': 'leaf', 'thrid': '2st'}
```

- `*args`에서는 **tuple**로 반환되었지만, `**kwargs`는 딕셔너리{}형태로 출력되었다

# input

`input`은 프로그램을 실행하고있는 User에게 특정한 값을 **입력받고자할때** 사용한다

형식

```python
변수 = input(내용1")
```

```python
"""result"""
내용1 
```

실행하면 내용1이 출력되고, User가 프로그램으로 넘겨주는 내용이 변수의 값으로 들어간다

```python
cow = input("black : ")
print(cow)
```

```python
"""result"""
black :
```

→ malan

```python
"""result"""
black : malan
malan
```

다른예제를 보자

```python
number1 = input("what is your favorite number? :")
print("your favorite number is " , number1)
print(type(number1))
```

→ 14

```python
"""result"""
what is your favorite number? :14
your favorite number is  14
<class 'str'>
```

- input으로 입력받은 변수의 내용은 **string형**이라는것에 주목해야한다

이부분에서 **Casting**을 사용해보도록하자

```python
number1 = int(input("what is your favorite number? :"))
print("your favorite number is " , number1)
print(type(number1))
```

```python
what is your favorite number? :17
your favorite number is  17
<class 'int'>
```

number1의 자료형을 기본형인 **str**에서 **int**형으로 **Casting**을 해줄 수 있었다.  


인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!  
