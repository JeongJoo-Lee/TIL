# RGB 거리
[백준 1149번](https://www.acmicpc.net/problem/1149)
* 분류 : 동적계획(DP)
## 나의 풀이(오답)
```python
n = int(input())
arr = []
dp = [0] * n

for i in range(n):
    RGB = list(map(int, input().split()))
    arr.append(RGB)

dp[0] = min(arr[0][0], arr[0][1], arr[0][2])
dp[1] = min(arr[0][0] + arr[1][1], arr[0][0] + arr[1][2],
            arr[0][1] + arr[1][0], arr[0][1] + arr[1][2],
            arr[0][2] + arr[1][0], arr[0][2] + arr[1][1])

dp[i] = dp[i-2] + min(arr[i-1][0] + arr[i][1], arr[i-1][0] + arr[i][2],
                    arr[i-1][1] + arr[i][0], arr[i-1][1] + arr[i][2],
                    arr[i-1][2] + arr[i][0], arr[i-1][2] + arr[i][1])

print(dp)
```
* 풀기전 삽질
```python
dp[0] = min(arr[0][0], arr[0][1], arr[0][2])
dp[1] = min(arr[0][0] + arr[1][1], arr[0][0] + arr[1][2],
            arr[0][1] + arr[1][0], arr[0][1] + arr[1][2],
            arr[0][2] + arr[1][0], arr[0][2] + arr[1][1])

dp[2] = dp[0] + min(arr[1][0] + arr[2][1], arr[1][0] + arr[2][2],
                    arr[1][1] + arr[2][0], arr[1][1] + arr[2][2],
                    arr[1][2] + arr[2][0], arr[1][2] + arr[2][1])

dp[3] = dp[1] + min(arr[2][0] + arr[3][1], arr[2][0] + arr[3][2],
                    arr[2][1] + arr[3][0], arr[2][1] + arr[3][2],
                    arr[2][2] + arr[3][0], arr[2][2] + arr[3][1]) 

dp[i] = d[i-2] + min(arr[i-1][0] + arr[i][1], arr[i-1][0] + arr[i][2],
                    arr[i-1][1] + arr[i][0], arr[i-1][1] + arr[i][2],
                    arr[i-1][2] + arr[i][0], arr[i-1][2] + arr[i][1])
```
> 다 써보면서 규칙 찾으려 했다.

![image](https://user-images.githubusercontent.com/61656046/111020809-c46e4600-840b-11eb-9489-5355743a6827.png)
* 예제에 대한 정답은 나오는데 저렇게 임의로 입력해버리면 dp 자료형이 중간에 빵꾸가 난다. 이유가 뭘까...

_ _ _
## 정답
```python
n = int(input())
p = []
for i in range(n):
    p.append(list(map(int, input().split())))
for i in range(1, len(p)):
    p[i][0] = min(p[i - 1][1], p[i - 1][2]) + p[i][0]
    p[i][1] = min(p[i - 1][0], p[i - 1][2]) + p[i][1]
    p[i][2] = min(p[i - 1][0], p[i - 1][1]) + p[i][2]
print(min(p[n - 1][0], p[n - 1][1], p[n - 1][2]))
```
* 빨강, 노랑, 초록 색깔마다 최솟값으로 접근해서 마지막에 또 min값을 적용시켜 정답을 출력하는 방법이다.

> 이런건 보자마자 떠오르는 건가 신기하다.




