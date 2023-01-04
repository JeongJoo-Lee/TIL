# 제로
[백준 10773번](https://www.acmicpc.net/problem/10773)
* 분류 : 스택
## 내가 푼 정답
```python
T = int(input())

stack = []

for i in range(T):
    N = int(input())
    if N == 0:
        stack.pop()                    # 0 이 입력되면 그냥 마지막꺼 지우고 0도 무시하고 넘어가면 끝
    else:
        stack.append(N)

print(sum(stack))
```
> 스택문제에 대한 적응을 어느정도 마친것 같다. 쉽게쉽게 풀린다.
