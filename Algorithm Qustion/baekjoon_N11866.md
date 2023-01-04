# 요세푸스 문제 0
[백준 11866번](https://www.acmicpc.net/problem/11866)
* 분류 : 큐
- - -

## 나의 풀이
```python
from collections import deque

N, K = map(int, input().split())

people = deque([x for x in range(1, N+1)])

result = []

print('<' ,end='')
while people:
    people.rotate(-(K-1))
    a = people.popleft()
    if not people:
        print(a, end='')
    else:
        print(a, end='')
        print(',' ,end=' ')

print('>')
```
> end 를 잘 써먹자
