# 나무자르기
[백준 2805번](https://www.acmicpc.net/problem/2805)
## 내가 제출한 오답
```python
import sys

def wood_cutting (array, M, start, end):
    check = []      # 나뭇가지 잘린거 모아놓는 집합
    H = (start + end) // 2   #중간값

    for h in array:         # 자른 나뭇가지 모아놓는 연산
        if h - H > 0:
            check.append(h)

    if sum(check) == M:   #만약 목표치보다 나뭇가지 더한것이 클 경우
        return H                #재귀함수로 end-1 범위로 수정 해준 값으로 연결(H값을 줄이기랑 자연스럽게 연결되게)
    elif sum(check) > M: #목표치와 나뭇가지 더한값이 같으면 자른 높이인 H를 리턴 max(array)-1 처럼 끝 수를 줄일것
        return wood_cutting(array, M, start, end-1)
    else:             #목표치보다 나뭇가지더한것이 작은 경우(H값에 1을 더하고 반복하게 재귀로 연결) start+1 처럼 시작 수를 늘릴것
        return wood_cutting(array, M, start+1, end)

N, M = map(int, sys.stdin.readline().split())
array = list(map(int, sys.stdin.readline().split()))
start, end = min(array), max(array)

print(wood_cutting(array, M, start, end))
```
* 이진탐색을 쓰려 재귀함수도 넣어보는 등...노력했지만 결국 구현해내지 못하였다.

## 정답
```python
import sys
# input 을 반복문으로 많이 받아야할 때 유용함
input = sys.stdin.readline
N, M = map(int,sys.stdin.readline().split())
tree_list = list(map(int,sys.stdin.readline().split()))
# 이분탐색법을 할 때는 임의로 left (min) & right (max) 값을 받아주고 중간값을 변경해가면서 알아내는 방식이다
min_val, max_val = 0, max(tree_list)
answer = 0
# 답은 아직 모르니 0 이라고 하자
while min_val <= max_val :
    # 중간값을 변화시켜야하니 루프 안에다가 넣어준다
    # *** 이렇게 min_val <= max_val 처럼 두 값이 같아버리게 설정하는 것은 왜 그럴까??
    mid_val = (min_val + max_val) // 2
    total_height = 0
    for tree in tree_list:
        if tree > mid_val:
            total_height += (tree - mid_val)

    if total_height >= M :
        answer = mid_val
        min_val += 1
    else:
        max_val = mid_val - 1

print(answer)
```
* 알고리즘 개념에 대해 좀더 확실히 숙지하고 응용해야 될 것 같음을 느꼈다. 아직 갈길이 너무 멀다..
