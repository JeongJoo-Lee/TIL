# 약수
[백준 1037번](https://www.acmicpc.net/problem/1037)
* 분류 : 정수론
## 내가 푼 답안
```python
N = int(input())
M = list(map(int, input().split()))

fin_number = 0
M.sort()        #약수들을 오름차순으로 정렬한다.

fin_number = M[0]*M[-1]    #오름차순으로 정렬된 약수들에서 첫째값과 끝에 값을 곱하면 무조건 결과가 나오게 된다.
print(fin_number)
```
> 어려운길로 갈뻔했는데 약수를 오름차순 정렬한 순간 부터 술술 풀렸다.
