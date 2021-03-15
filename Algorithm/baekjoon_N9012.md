# 스택
[백준 9012번](https://www.acmicpc.net/problem/9012)
* 분류 : 스택
## 내가 푼 풀이
```python 
from sys import stdin

stack = []
result = []

N = int(input())

for i in range(N):
    VPS = list(stdin.readline().rstrip())
    if VPS[0] == ')':
        result.append('NO')
        continue

    for j in range(1, len(VPS)):
        if VPS[j-1] == '(' and VPS[j] == ')':
            stack.append(0)

        elif VPS[j-1] == '(' and VPS[j] == '(':
            stack.append(1)

        elif VPS[j-1] == ')' and VPS[j] == ')':
            stack.append(-1)

        elif VPS[j-1] == ')' and VPS[j] == '(':
            stack.append(0)
        else:
            continue

    if sum(stack) == 0:
        result.append('YES')
    else:
        result.append('NO')

for i in result:
    print(i)
```
> 나는 조합을 보고 stack에 +1, -1 을 넣어줌으로서 stack의 합이 0 인지 아닌지에 따라 결과물을 출력하는 방법으로 접근하였고, 예제는 다 맞았으나 제출과정에서 틀렸다.
>> 원인은 아직 찾지 못했다. 비슷한 풀이가 없을까 해서 구글링을 해보니 아래 풀이가 나오더라.


- - -
## 비슷한 접근법의 정답
```python
a = int(input())
for i in range(a):
    b = input()
    s = list(b)
    sum = 0
    for i in s:
        if i == '(':
            sum += 1
        elif i == ')':
            sum -= 1
        if sum < 0:             #시작부터 ')' 이면 아예 보질 않겠다.
            print('NO')
            break
    if sum > 0:
        print('NO')
    elif sum == 0:
        print('YES')
```
> '(' 인자 하나하나에 +1, -1 에 대한 값을 넣고 풀었다. 이방법이 훨씬 직관적이고 덜 복잡한 방법인것같긴하다. 내가 생각했던 방법이랑 비슷하여 
> 코드 자체는 금방 이해가 되었으나 내 코드보다 어떤점에서 더 완벽함을 가지고 있는지 정의하지 못하겠다. 아직 통찰력이 부족한듯 하다.
>> 이런풀이도 가능하겠구나 라며 또 배웠다.
