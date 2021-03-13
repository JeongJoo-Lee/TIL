# 동전0
[백준 11047번](https://www.acmicpc.net/problem/11047)
* 분류 : 그리디 알고리즘
## 내가 푼 답안
```python
from sys import stdin
read = stdin.readline

N, K = map(int, input().split()) #동전갯수와 값 입력
coin_list = list((int(read()) for x in range(N))) #동전 종류 입력받기
count = 0

coin_list.sort(reverse=True)

for i in range(N):
    if K == 0:
        break
    
    if coin_list[i] > K:
        continue
    else:
        count += K//coin_list[i]
        K %= coin_list[i]
    
    
print(count)
```
* 처음엔 재귀함수로 접근해보려다 재귀에 아직 미숙한 나머지 생각이 미로에 빠져 포기
* 이후 반복문으로 잘 풀었으나 이상하게 계속 백준 채점에서 틀렸다고 나왔다.
* 몇시간의 디버깅 끝에 이유를 알게됨
> for문에서 range(N) 부분에 range(N-1) 을 적어뒀던 것. 
> 내림차순으로 정렬하기 전에 역으로 반복 돌기위해 range(N-1, -1, -1) 을 설정하다 좀 헷갈려 고치는 과정에서 -1을 안빼줬던 것이 화근이었다.
* **range() 범위에 대한 개념**을 다시 잡는 시간이 필요할 듯 하다.
