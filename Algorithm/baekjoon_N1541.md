# 잃어버린 괄호
[백준 1541번](https://www.acmicpc.net/problem/1541)
* 분류 : 그리디 알고리즘

<br>

- - -


## 내가 푼 풀이 
```python
N = list(input())

stack = []

for n in N:
    if '-' not in stack and n == '-':
        stack.append(n)
        stack.append('(')
    
    elif '-' in stack and n == '-':
        stack.append(')')
        stack.append(n)
        stack.append('(')

    elif '-' in stack and n == N[-1]:
        stack.append(n)
        stack.append(')')
    
    elif n == '0':
        if stack[-1] == '(' or stack[-1] == ')' or stack[-1] == '+' or stack[-1] == '-':
            continue    
        elif not stack:
            continue
    else:
        stack.append(n)
        
result = ''.join(stack)

print(result)
```
> 문자열을 숫자열로 계산하는 방법을 당시에는 몰랐다. **eval()** 이라는 좋은 함수가 있을줄은... 따로 공부 예정
<br>

- - -


## 다른사람 풀이
```python
a = input().split('-')
num = []
for i in a:
    cnt = 0
    s = i.split('+')
    for j in s:
        cnt += int(j)
    num.append(cnt)
# 첫번째 값을 따로 뺴주고
n = num[0]
# 이후의 값들과 첫번째값을 모두 (-) 계산해서 n 을 출력하면 정답
for i in range(1, len(num)):
    n -= num[i]
print(n)
```
> 괄호를 쓰지 않고 split()을 이용해 괄호처럼 활용하여 문제를 해결하였음
