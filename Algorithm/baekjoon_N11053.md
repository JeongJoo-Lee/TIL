# 가장 긴 증가하는 부분수열(LIS)
[백준 11053번](https://www.acmicpc.net/problem/11053) 
* 분류 : DP

- - -

## 나의 풀이
```python
from sys import stdin

N = int(input())
nums = list(map(int, stdin.readline().split()))

dp = [1]*N

for i in range(N):
    for j in range(i):
        if nums[j] < nums[i]:
            dp[i] = max(dp[i], dp[j] + 1)

print(max(dp))
```
> 예전 SSAFY 준비할때 배웠던 내용이라 접근하는데 어려움은 없었다. 자세한내용은 블로그에 포스팅하였음.

[블로그](https://data-jj.tistory.com/39)
