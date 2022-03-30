---
layout: post
title:  "인프런 리프2기 2. Print"
subtitle:   "인프런 리프2기"
categories: python
tags: leaf2st
comments: true
---


# 이번시간에는 출력을 해보도록하자!

1. print함수
2. print함수의 속성, sep
3. format
4. variable
5. id

# print함수

파이썬에서는 콘솔에 출력할수 있게 `print` 라는 기능을 제공한다 

print() 는 ()안에 있는 내용을 콘솔로 출력해 주는 기능이다

각자의 코드 에디터에 다음과 같이 작성한 이후에 코드를 실행해보자
(코드를 실행하는 방법은 Vscode기준으로 Ctrl + F5 키를 동시에 누른다)

```python
print('Python Start!')
```

- `print`라는 함수 안에
- `'`(따움표 , apostrophe) 두개로 감싸진
- `Python Start!` 라는 텍스트

```python
"""result"""
Python Start!
```

- 콘솔로 Python Start! 라는 내용이 출력되었다는점을 확인할수있다

하나만하지말고, 다른것도 더 해보자

```python
print('Python Start!') 
print("Python Start!") 
print("""Python Start!""")
print('''Python Start!''')
```

이번엔 따움표1개, 쌍따움표1개, 쌍따움표3개, 따움표3개를 한꺼번에 출력해보도록 하자

```python
"""result"""
Python Start!
Python Start!
Python Start!
Python Start!
```

따움표의 종류와 관계없이 출력이 된것을 볼수있다

그러면 이런실험을 해보자.

```python
print('Python Start!') print("Python Start!")
```

이번에는 print두개를 한줄에 쓰는거다. 위에서 에러가 안났으니까, 상관없지않을까? 하고 코드를 실행해보자

```python
"""result"""
File "c:\Users\kmkimlane\Desktop\pypyfloder\section3.py", line 1
    print('Python Start!') print("Python Start!")
                           ^
SyntaxError: invalid syntax
```

- 어떤 파일에서 에러가 났는지(c:\Users\kmkimlane\Desktop\pypyfolder의 section2.py)
- 어떤 내용에서 에러가 났는지 (print('Python Start!') **p**rint("Python Start!") )
- 에러의 종류는 무엇인지 ( invalid syntax)

# Separator

print문내부에서는 ,로 이어져만있으면 한번에 쭉~ 출력하되, 띄어쓰는것을 확인할수 있다.

이때 sep메소드를 써서 출력하는 옵션을 설정해줄수 있다. 직접 확인해보자.

```python
print('inflearn',"Leaf",'2st')
print('inflearn',"Leaf",'2st',sep='')
print('inflearn',"Leaf",'2st', sep='-')
print('inflearn',"Leaf",'2st', sep=' to the ')
```

- 첫번째 print는 따움표(')와 쌍따움표(")가 섞여있고
- 두번째 print는 첫번째print에서 ,`sep=''` 를 작성해주었다
- 세번째 print는 두번째print에서 sep의 '' 내부에 `-` 를 작성해줬다
- 네번째 print는 세번째print에서 `-` 대신에  `to the` 를 작성해주었다.

```python
"""result"""
inflearn Leaf 2st
inflearnLeaf2st
inflearn-Leaf-2st
inflearn to the Leaf to the 2st
```

- 첫번재는 각각의 내용이 띄어쓰기 되있고
- 두번째는 각각의 내용이 붙혀져서 나오고
- 세번째는 -로 연결되서 나오고
- 네번째는 to the 로 연결되서 나온다

# format

print함수에서 중요한것중 하나는 format을 직접 지정해주는것이다.

%s는 문자열을 출력하고, %d는 정수형을, %f는 부동소숫점형을 나타내주는 일종의 출력도구이다

```python
print('%s %s' % ('one', 'two'))
print('{} {}'.format('one', 'two'))
print('{1} {0}'.format('one', 'two'))
```

- `%s` : 문자열(text)를 출력하겠다
- `% ('one', 'two')` : 문자열의 내용은 one 과 two 이다
- `{}` : 무슨내용이 들어갈지는 모르지만 어떠한 내용이 나올것이고, 추후에 설명하겠다
- `.format('one', 'two')` : 앞서나온{}의 내용이 `'one'`과 `'two'`이고, 'one'은 첫번째로 나온원소니 0의 인덱스를 할당하고, 'two'는 두번째로 나온원소니 1의 인덱스를 할당하겠다
- `{1} {0}` : {}를 원래는 순차적으로넣어야하는데, 인덱스를 명시해줬으니, 인덱스에 맞게 출력해주겠다

강의내용에서는 format이외에 %d, %f, %s 이외에도 %.3s 나 %06.2f 를 알려주는데 이부분은 생략하겠다. 알고만 넘어가도 되는 부분이기도하고, 꼭 필요한 부분은 아니라고 생각하기 때문이다.

# Variable

이번엔 자료형을 선언하고 출력해보도록하자

선언하는 형식은 `=` 기호를 사용한다

`왼쪽` `=` `오른쪽` 이렇게 되어있으면, 왼쪽에 있는**'변수'**가 오른쪽에 있는 **'내용'**을 가진다고 한다.

(이건 파이썬의 규칙이다)

```python
Q = 100
W = "Inflrean"
E = 10.5
R = Q
```

`Q`라는 변수에는 `100` 이라는 내용(숫자**.정수**) 를 주었고

`W`라는 변수에는 `"Inflearn"` 이라는 내용(**텍스트**) 를 주었고

`E`라는 변수에는 `10.5` 라는 내용(숫자.**소수**)를 주었고

`R`라는 변수에는 `Q`라는 내용(**변수**)를 주었다

```python
Q = 100
W = "Inflrean"
E = 10.5
R = Q

print(Q,W,E,R)
print(type(Q),type(W),type(E),type(R))
```

이런식으로 변수를 출력해보고, 자료형을 type메소드를 써서 출력해보자

```python
"""result"""
100 Inflrean 10.5 100
<class 'int'> <class 'str'> <class 'float'> <class 'int'>
```

이번엔 변수를 다시 정의해보자. 

```python
Q = 100
W = "Inflrean"
E = 10.5
R = Q

print(Q)
Q = 150
print(Q)
```

```python
"""result"""
100
150
```

첫번째 나온 `Q`는 `100`을 가지고있지만, 두번째 나온 `Q`는 `150`을 가지고있다.

이는 **print의 성질**이고, 실행한 print함수 기준으로 **가장 최근의 값**을 나타내는 print의 성질을 이용한것이다.

# ID

우리는 `왼쪽` `=` `오른쪽` 에서 오른쪽의 `내용`을, 왼쪽의 `변수`에 넣는다고 배웠다.

이 부분은 그것을 구별하는 가장 중요한 내용이다. 변수의 고유주소를 알수있는 부분이다.

```python
Q = 100
E = 100
R = Q

print(Q,E,R)
print(id(Q))
print(id(E))
print(id(R))

R=150
print(Q,R)
print(id(Q))
print(id(R))

Q=200
print(Q,R)
print(id(Q))
print(id(R))
```

E와 Q는 `100` 이라는 값을 공통으로 가지고, `변수`R은 Q의 `내용`을 가진다.

```python
"""result"""
100 100 100
140723765318400
140723765318400
140723765318400
100 150
140723765318400
140723765320000
200 150
140723765321600
140723765320000
```

처음엔, QER은 모두 같은값이고id가 모두 동일하다.

R=150선언이후, Q와R은 다른값을가지고, id가 서로다르다

Q=200선언이후, Q와R은 다른값을가지고, id가 서로다르다.

이는 개체 참조에서 나오는 내용인데, 지금은 일단 다르다는것만 알고 넘어가자


인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!  

