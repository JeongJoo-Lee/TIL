# 가장 긴 바이토닉 부분 수열
[백준 11054번](https://www.acmicpc.net/problem/11054)
* 분류 : DP
- - - 
## 나의 풀이
```python
import sys

N = int(input())

num_list = list(map(int, sys.stdin.readline().split()))


dp = [1]*N
reverse_dp = [1]*N

# 정방향 dp 구하기
for i in range(N):
    for j in range(i):
        if num_list[j] < num_list[i]:
            dp[i] = max(dp[i], dp[j] + 1)


# 역방향 dp 구하기
num_list.reverse()
for i in range(N):
    for j in range(i):
        if num_list[j] < num_list[i]:
            reverse_dp[i] = max(reverse_dp[i], reverse_dp[j] + 1)

reverse_dp.reverse()

result = [x+y for x,y in zip(dp, reverse_dp)]
print(max(result)-1)
```

## 접근 방법
```
# 입력된 리스트를 하나하나 보면서 해당 값이 좌측 기준으로 몇번째로 큰지
# 우측기준으로 몇번째(서열) 인지 구해서 각각 리스트에 저장해둔다.
# 그리고 그 두개의 리스트를 같은자리 인자들끼리 모두 더한다음
# 최댓값을 구하고
# 최댓값에서 1을 빼주면 가장 긴 바이토닉 수열 길이가 출력된다.
```
