---
layout: post
title:  "코딩테스트 라이브러리 모음집"
subtitle:   "Codingtest"
categories: pypy
tags: codingtest
comments: true
---
# 코딩테스트에 필요한 잡기술을 먼저 배워보도록 하자  


# dfs,bfs 공통 dataset

```python
graph = [
    [], #0번째 노드는없음
    [2,3,8],[1,7],[1,4,5],[3,5], [3,4],[7],[2,6,8],[1,7]
]
visited = [False] * 9
```

# dfs

```python
def dfs(graph,v, visited) :
    visited[v] = True
    print(v)
    
    for i in graph[v] :
        if not visited[i] :
            dfs(graph,i,visited)

#dfs(graph,1,visited)
```

깊이탐색. 네트워크안에서의 갯수를 세는 전형적인 방식

# bfs

```python
from collections import deque
def bfs(graph,start, visited) :
    queue = deque([start])
    visited[start] = True
    
    while queue : 
        v = queue.popleft()
        print(v)
        for i in graph[v] :
            if not visited[i] :
                queue.append(i)
                visited[i] = True

#bfs(graph,1,visited)
```

너비탐색. 최단거리의 길이를 찾는 전형적인 방식

# sorted, sort

```python
sorted([1,5,2,4,3])
# [1,2,3,4,5]
sorted([1,5,2,4,3], reverse =True)
# [5,4,3,2,1]

data = [9,5,7,2] 
data.sort()
# data = [2,5,7,9]
```

# heapq

```python
import heapq

def heapsort(iterable) :
    h = []
    result = []
    for value in iterable :
        heapq.heappush(h, value)
        print(h)
    for i in range(len(h)) :
        result.append(heapq.heappop(h))
    return result

result = heapsort([1,3,5,2,4,6])
print(result)
```

 우선순위큐 O(n logn)

# bisect

```python
from bisect import bisect_left, bisect_right
a = [1,2,4,4,7]
print(bisect_left(a,4))
#2
print(bisect_right(a,4))
#4
```

특정 원소값 의 좌우 인덱스 확인

# Enumerate

```python
names = ['JJong', 'Guet', 'kmkimlane']
for i, name in enumerate(names) :
	# i = 0, name = 'JJong'
	# i = 1, name = 'Guet'
	# i = 2, name = 'kmkimlane'

```

i,j,name 이런식으로하면 value error나옴

# for

```python
points =[(1,4),(10,40),(2,20),(6,60)]

for x,y in points :
	# x = 1, y = 4
	# x = 10, y = 40
	# x = 20, y = 20
	# x = 6, y = 60
```

# zip

```python
columns = ['name','share','food']
values = ['good','nice','wrong']
pairs = zip(columns, values)

# pairs = ('name','good'), ('share','nice'), ('food','wrong')

for i,j in pairs:
    # i = name, j = good
    # i = share, j = nice
    # i = food, j = wrong

d = dict(pairs)
# d = {'name':'good', 'share':'nice', 'food':'wrong'}
```

# Dict reverse

```python
price = {
    'good' : 15, 'nice' : 10, 'oh' : 5
}

price_reverse = zip(price.values(), price.keys())
price_reverse = list(price_reverse)
print(price_reverse)
```

단순히 zip으로 만들면, 얘네가 단순히 객체로 인식해서

얘를 보려면 다른식으로 만들어야함 → set, list, dict ...

# collections

```python
from collections import Counter

cnt = Counter()
for word in ['red', 'blue', 'red', 'green', 'blue', 'blue']:
    cnt[word] += 1
```

중복제거하기 매우 좋은거같음. (중복제거하는 또다른방법은 list나 set에서 in 쓰는방법)

```python
from collections import defaultdict

Normal_dict = collections.defaultdict(int)
normalKey = ['a','b','c']
for i in normalKey : 
    Normal_dict[i]
print(Normal_dict)
#defaultdict(<class 'int'>, {'a': 0, 'b': 0, 'c': 0})
```

# deque

```python
from collections import deque
a = [1,2,3,4,5]
q = deque(a)

q.rotate(2) # 4,5,1,2,3 ->방향이동

q.append(6) # 4,5,1,2,3,6

q.appendleft(10) #10,4,5,1,2,3,6

q.pop() #10,4,5,1,2,3

q.popleft() #4,5,1,2,3
```

list (일찍들어간애가 나중에 나오는거)

queue (일찍들어간애각 맨먼저 나오는거)

를 합친 애가 deque(rotate, append, appendleft, pop, popleft)

아무리생각해도 개꿀같은데?

# itertools

`import itertools`

```python
import itertools 

list_a = ['a','b','c']
list_1 = [1,2,3]

list(itertools.chain(list_a,list_1))
#['a','b','c',1,2,3]
```

```python
from itertools import product
l1 = ['A','B']
l2 = ['1','2']
for i in product(l1,l2) :
    print(i)
#('A', '1')
#('A', '2')
#('B', '1')
#('B', '2')
```

```python
from itertools import permutations
data = ['A','B','C']
result = list(permutations(data)

->
[('A', 'B', 'C'),
 ('A', 'C', 'B'),
 ('B', 'A', 'C'),
 ('B', 'C', 'A'),
 ('C', 'A', 'B'),
 ('C', 'B', 'A')]
```

프로그래머스 행렬의덧셈

```python
arr1 = [[1,2],[3,4]]
arr2 =[[5,6],[7,8]]
print(arr1)

for i in range(len(arr1)) :
    for j in range(len(arr1[0])) :
        arr1[i][j] += arr2[i][j]

print(arr1)
print(arr2)
```

튜플에서의 값변경

```python
arr = [('hong',9),('kim',4)]
arr = sorted(arr, key=lambda x : x[1])
arr
#[('kim',4),('hong',9)]
```