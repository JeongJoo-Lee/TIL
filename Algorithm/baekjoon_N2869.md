# 달팽이는 올라가고 싶다.
[백준 2869번](https://www.acmicpc.net/problem/2869)

## 처음 시도했던 답안

```python
A, B, V = map(int, input().split())

cnt = 0
location = 0

while True:
     location += A
     cnt += 1
     if location >= V:
         break
     else:
         location -= B

print(cnt)
```
* 결과 : 시간초과
  * 시간 복잡도를 고려하지 않고 무자비하게 while 문을 사용하였다.



## 이후 푼 정답

```python
UP, DOWN, GOAL = map(int, input().split())

DAY = (GOAL-DOWN)/(UP-DOWN)
print(int(DAY) if int(DAY) == DAY else int(DAY) + 1)
```
* 최대한 시간복잡도를 높이지 않기 위해 반복문을 사용하지 않기위해 고민하였다.
* 처음으로 시간복잡도를 생각하고 풀게 된 문제였다. 앞으로도 쭉 고민하게 되겠지


