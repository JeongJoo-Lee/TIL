# ATM
[백준 11399번](https://www.acmicpc.net/problem/11399)
* 분류 : 그리디 알고리즘

## 내가 푼 답안
```python
N = int(input())
people = list(map(int, input().split()))

people.sort()
temp = []
result = []

for i in people:
    temp.append(i)             # temp 에 i 를 담는다.
    num_sum = sum(temp)        # temp에 담긴 i 값들의 합을 num_sum 변수에 입력한다.
    result.append(num_sum)     # i 번째 까지의 합이 result 안에 담긴다.(자신포함 앞자리 숫자들을 더한 모든 값들이 차례대로 들어옴)   

print(sum(result))
```
* 쉽게 생각했다가 의외로 고전했던 문제, 침착하게 다시 보니 temp 변수에 임시로 담았다가 빼주는 작업을 넣어줌으로서 해결되었다.
* 그리디문제는 생각하는게 재미있다.
