# 다리 놓기
[백준 1010번](https://www.acmicpc.net/problem/1010)
* 분류 : 동적계획법, 조합론
## 나의 풀이
```python
def factorial(num):
    n = 1
    for i in range(1, num+1):
        n *= i
    return n

result = []

T = int(input())
for i in range(T):
    N, M = map(int, input().split())
    if N < M:                                     # N이 M보다 작을경우 전혀 다른 결과가 나와서 추가한 조건임
        (N, M) = (M, N) 
        pass

    result_num = factorial(N)//factorial(N-M)//factorial(M)     # 11050번 문제와 같음. 이항계수처럼 N개 에서 M개를 뽑을때의 경우의 수
    result.append(result_num)

for i in result:
    print(i)

```
[개념 참고한 블로그](https://zifmfmphantom.tistory.com/13)
> 이항계수의 개념으로 풀었다. 다른방법도 시도하려했지만 구현이 좀 어려워서 실패했다. 이항계수의 공식이나 개념정도는 확실히 인지하고 넘어가야 할듯 하다.
