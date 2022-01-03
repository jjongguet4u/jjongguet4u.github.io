---
layout: post
title:  "인프런 리프2기 8~9.Function && File IO"
subtitle:   "인프런 리프2기"
categories: out
tags: leaf2st
comments: true
---

# Built-in함수와 External함수

함수는 내장함수(Built-in Function)와 외부함수(External Function) 이렇게 두종류의 함수로 구분된다.

**Built-in Function**는 따로 불러오지않아도 사용할수 있다.

예를들면 절댓값으로 반환하는 `abs()`, 인덱스와 Iterable한 객체를 만들어내는 `enumerate()`가 있다. 

일종의 키워드 들도 Built-in Function으로 기준잡는것같다. 예를들면 

`in, range, sum, print`와 같은 것들이다.

**External Function**은 따로 불러와서 파이썬에서 사용할수 있는것들이다.

가령 예를들어서 `sys` 를 쓰고싶으면

```python
import sys
print(sys.argv)
```

이런식이다.

아니면 뭐 소스코드에서 쉬는시간을 주려면

```python
import time
for i in range(5) :
	print(i)
	time.sleep(10)
```

이런식으로 time을 활용해서 time.sleep()을 쓸수도있다.

아니면 random함수를 통해서

```python
import random
print(random.randint(1,45))
```

이런식으로 랜덤한 값을 print할수도 있다

이런방식으로 import해서 쓰는것들이 External-Function라고 통칭한다.

크롤링만 가봐도 beautifulsoup이나 selenium많이쓰니까 예제 찾아서 해보면 재밌을것같다

# 파일입출력

보통은 파일입출력 부분은 File Input, Output으로 표현하는데 I와 O를 줄여서 File IO라고 부른다

여담으로 C언어에서는 `#include <stdio.h>` 를 쓰는데 여기서 <stdio.h>는 **st**an**d**ard **i**nput **o**utput 의 약자를 가진 header파일이다.

파일을 다룰려면 먼저 주로쓰는 **3가지 모드**를 알아야한다.

1. **읽기전용모드 r** 

    → 파일을 읽기만함

2. **쓰기전용모드 w**

    → 파일에서 쓰기만함

3. **추가모드 a**

    → 파일에서 1와2를 동시에 제공한다

이 3가지 모드는 서로 다른 기능을 제공한다.

그리고 또 하나 알아야할것은 **상대경로, 절대경로** 개념이다

예를들어 내가 실행하고있는 로컬 경로가 바탕화면이면

`C:\Users\쫑긋\Desktop` 이 현재 프로그램이 위치한 경로이고

바탕화면에서 **STUDY**란 폴더에 접근하게되면 경로는 `C:\Users\쫑긋\Desktop\STUDY` 가 된다.

이때, 내가 프로그램을 실행했던 경로에서 STUDY폴더에 접근하고싶을때

상대경로로 접근하게된다면 `('./STUDY')`로 접근하면 될것이고

절대경로로 접근하게된다면 `('C:\Users\쫑긋\Desktop\STUDY')` 로 접근하게 될것이다.

A.txt파일

```python
hello i'm JJong Geut
Nice To Meet You
Inflearn
```

접근예제

- 상대경로로 A.txt에 접근하기

```python
f = open('A.txt','r', encoding='UTF-8')
print(f.name)
print(f.mode)

f.close()
```

`f = open` : 파일의 상대경로를 넣어서 파일을 넣음

[`f.name`](http://f.name) : 파일의 이름 return

`f.mode` : 파일의 모드 return

이때 주의해야할점 `f.close` 는 파일이 차지한 메모리를 다시 반환해주는것이다

open할때 메모리를 할당해줬으므로, close로 메모리를 돌려넣는다 라는 개념으로 이해하면 된다.

읽기예제

```python
with open('A.txt', 'r', encoding='UTF-8') as f:
    line = f.readline()
    print(line)
    line = f.readline()
    print(line)
```

```python
"""result"""
hello i'm JJong Geut

Nice To Meet You
```

상단에서는 `with — as — :` 구문을 사용했다.

이 구문을 쓰게되면, tab으로 들어간 부분이 끝나면 파일이 할당된 메모리를 자동으로 반환한다

`realine()` : 한줄을 읽어서 가져온다

지금 파일에는 총 3줄로 구성되어있지만, `f.readline()`으로 읽어온 줄이 2줄밖에 없어서 2줄만 출력되었다

이번에는 쓰기예제를 해볼것이다

그러기위해서 빈 파일인 B.txt를 만든다

B.txt파일

```python

```

쓰기예제

```python
with open('B.txt', 'w') as f:
    f.write('I love python\n')
```

B.txt를 열어서, f.write() 함수로 덮어쓰기를 진행할것이고

그 내용은 **'I love python\n'**이다.

B.txt파일

```python
I love python

```

이때 주의해야할점은 \n도 들어갔다는것이다. python출력이후에 줄바꿈(\n)이 적용되었다.

이번에는 CSV파일을 읽어볼것이다.

C.csv파일

```python
index, phone
1, Apple
2, Samsung
3, Google
4, hwawei
```

CSV파일은 보통 엑셀파일이라고 생각하면된다. 그래서 일반적으로 각각의 line의 형태가 비슷하다는 특징이 있다.

```python
with open('C.csv', 'r') as f:
    reader = csv.reader(f, delimiter=',')
    
    for c in reader:
        # print(c)
        print(''.join(c))
```

이때 확인해야하는 내용중에 `delimiter=','` 에 주목해야한다

 일반적으로 **.csv**파일은 각자의 파일마다 구분자 라는것이 존재한다.

C.csv파일은 **각각의 줄을** `\n`으로 구분하고있고, **숫자와 문자열을** `,`로 구분하고있다

그래서 내용을 한줄씩 읽고, 구분자속성인 **delimiter** 속성을 이용해서

**첫번째단어, 두번째단어**를 구분하는것이다.

# VSCode에서 .csv가 안먹힌다...?

필자는 에디터로 VSCode를 사용하고있고, 여태까지 모든 소스코드작업을 VScode에서 사용했다

그러나....!

VSCode에서는 csv파일을 못읽는것같다.. 

위에 적은 내용은 강의영상에서보고, 작성한 것이지만

실제 소스코드로 돌려보면 에러가 난다 ㅜㅜ

csv파일 실습은 여기서 마무리해야할것같다.  

마지막 Section은 여태까지 배운 내용으로 작은 미니게임을 진행하는것인데, 이 부분은 각자 해보길 바란다...!  



인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!  
