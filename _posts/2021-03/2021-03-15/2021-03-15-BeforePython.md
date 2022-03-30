---
layout: post
title:  "인프런 리프2기 0. 설치부터 실행까지"
subtitle:   "인프런 리프2기"
categories: python
tags: leaf2st
comments: true
---


# 프로그래밍 공부에 앞서

프로그래밍을 공부할때 가장 우선적으로 정할 2가지는

1. 어떤 언어를 공부할것인가?
2. 어떤 개발환경을 사용할것인가?

에 대한 고민이다.

본격적인 개발환경 구축을 해보자!

# VSCODE 설치

코드 에디터로는 Atom대신에 Visual Studio Code를 사용할것이다.

Visual Studio Code의 줄임말로는 VSC, VSCode 등... 줄임말도 꽤 있는데 

Visual Studio와 다르단 것만 알아두면 된다.

[https://code.visualstudio.com/](https://code.visualstudio.com/)

위 링크에가서
<img src="/assets/img/202103/0315/1VSC.jpg">  


각자 설치환경에 맞는 버전을 다운로드하자

# Python 3.8.6 설치

파이썬 공식홈페이지 [https://www.python.org/](https://www.python.org/) 에 들어간다음

Download탭을 보면 Latest: Python 3.9.2 라고 적혀있는것을 볼수있다.

<img src="/assets/img/202103/0315/2Python.jpg">  

가장 최근버전인 3.9.2대신에, 가장 Stable인 3.8.6버전을 다운로드받아주겟따

[https://www.python.org/downloads/release/python-386/](https://www.python.org/downloads/release/python-386/)

이 링크에 들어가서 → Files 항목을 찾는다 

여기서 각자의 버전에 맞는 프로그램을 다운로드한다.


<img src="/assets/img/202103/0315/3version.jpg">  

(윈도우10을 사용하고 있고, 64bit의 컴퓨터를 사용하고있다면, Windows x86-64 executable installer를 선택해서 설치한다')

**이때 주의할점**

설치를 하다보면 이런창이 뜨게된다.

<img src="/assets/img/202103/0315/4Attention.jpg">  

(사진은 파이썬 3.8.0 설치시 나오는 화면이다)

이런창이 뜨게되면 하단의 체크박스의 Add Python 3.8 to PATH를 눌러주고, 상단의 Install Now를 눌러줘야한다

이 부분은 환경변수 등록하는 부분인데, 이부분을 안해주면 환경변수를 직접 잡아줘야해서 귀찮아진다.

여기까지했으면 설치는 끝났다...! 

세부설정을 해주도록 하자

# VSCode → 세부설정

VSC → 확장 → 'Python'검색후 설치
<img src="/assets/img/202103/0315/5marketplace.jpg">  

Python을 Vscode에서 사용할수 있도록 설치하는 내용이다 꼭 설치하도록 하자.

밑의 사진은 필자의 확장탭이다. 

필자는 C/C++ 부터 Remote-WSL까지 다양하게 설치해놓은것을 볼수있다.

<img src="/assets/img/202103/0315/6Extension.jpg">  

# 폴더설정

바탕화면에 파이썬 전용 폴더를 하나 만들어주자

필자는 pypyfolder라고 정해놨다

<img src="/assets/img/202103/0315/7pypyfolder.jpg">  

이제 pypyfolder와 VSCODE를 연결해줄것이다

우선, VSCODE를 실행해주자

<img src="/assets/img/202103/0315/8IMG1.jpg">  

여기서 상단의 파일-폴더열기-아까만들었던 pypyfolder 를 눌러준다

<img src="/assets/img/202103/0315/8IMG2.jpg">  

(얍! pypyfolder가 열렸다)

시험삼아 python 파일 하나 만들어서 돌려보자

1. 탐색기→ 우클릭 → 새파일 → [0315.py](http://0315.py) (오늘날짜)
2. 코드 타이핑

    ```python
    print("Hello World")
    print("With Inflrean Leaf 2st")
    ```

3. 세이브 : Ctrl + S 
4. 실행 : Ctrl + F5

<img src="/assets/img/202103/0315/8IMG3.jpg">  

Hello World

With Inflearn Leaf 2st 

라고 출력됨을 볼수있다!

(필자는 설정을 달리해서 하단의 터미널창에서 파란색 어쩌구저쩌구 나오는데, 이부분은 신경안써도된다)  

인프런 공식 사이트로 이동은 [여기](https://www.inflearn.com/)를 클릭해주세요!  
인프런 리프2기에서 하는 인프런 파이썬 입문 강의로 이동은 [여기](https://www.inflearn.com/course/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%AC%B8-%EC%9D%B8%ED%94%84%EB%9F%B0-%EC%98%A4%EB%A6%AC%EC%A7%80%EB%84%90)를 클릭해주세요!  
