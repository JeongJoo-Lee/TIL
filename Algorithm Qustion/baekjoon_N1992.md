# 쿼드트리
[백준 1992번](https://www.acmicpc.net/problem/1992)
* 분류 : 분할정복, 쿼드트리
<br>

- - -

## 나의 풀이
```python
from sys import stdin

N = int(input())

square = [list(map(int, input())) for _ in range(N)]


def check(x, y, N):
    compare_value = square[x][y]
    for i in range(x, x+N):
        for j in range(y, y+N):
            if square[i][j] != compare_value:
                return False
    return True


def solve(x, y, N):
    if check(x, y, N):
        if square[x][y] == 0:
            print(0, end='')
            
        else:
            print(1, end='')
        return
     
    else:
        print('(',end='')   
        N //= 2
        solve(x, y, N)
        solve(x, y + N, N)
        solve(x + N, y, N)
        solve(x + N, y + N, N)
        print(')',end='')    
        return



solve(0, 0, N)
```
> 색종이 문제와 거의 흡사한 로직으로 풀었더니 풀렸다.
