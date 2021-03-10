# 회전하는 큐
[백준 1021번](https://www.acmicpc.net/problem/1021)
## 나의 정답(처음으로 맞춤...!)
```python
import sys
N, M = map(int, input().split())                           # 큐의 크기(N)
target = list(map(int, sys.stdin.readline().split()))      # 뽑아내려 하는 값(M)
queue = [x for x in range(1, N + 1)]                        # 큐

count = 0

for i in target:
    while i in queue:                             # i가 queue안에 있는한 계속 반복
        if queue[0] == i:                           # 첫위치에 타겟이 있으면 빼버리기
            queue.pop(0)                             
        
        elif queue.index(i) > len(queue)//2:         # i의 위치가 중앙값보다 우측에 있으면 우측이동
            queue.insert(0, queue[len(queue)-1])
            queue.pop()
            count += 1                              #이동하면서 계속 count up
        
        elif queue.index(i) <= len(queue)//2:       # i의 위치가 중앙값보다 좌측에있으면 좌측이동
            queue.append(queue[0])
            queue.pop(0)
            count += 1

print(count)
```

* **deque.ratate** 를 써야되는지 몰라서 자체적으로 생각해낸 기능
```python
# a=[1,2,3,4,5,6]

# #우측으로 한칸 밀기
# a.insert(0, a[len(a)-1])  [6,1,2,3,4,5,6]        #insert(추가할위치, 추가할 값)
# a.pop(-1)                 [6,1,2,3,4,5]
# print(a)


# b=[1,2,3,4,5,6]
#좌측으로 한칸 밀기
# b.append(b[0])  #[1,2,3,4,5,6,1]
# b.pop(0)         #[2,3,4,5,6,1]
# print(b.index(5))
```

## 다른사람의 정답(deque.ratete 활용 답안)
```python
import sys
from collections import deque
n, _ = map(int, sys.stdin.readline().split())
numbers = list(map(int, sys.stdin.readline().split()))
queue = deque(range(1, n+1))

total_compute = 0

for idx in range(len(numbers)):
    if numbers[idx] == queue[0]:
        queue.popleft()
        continue
    queue_idx = queue.index(numbers[idx])

    # 뒤 -> 앞으로 옮기는 게 이득인 경우
    if queue_idx > len(queue) // 2:
        queue.rotate(len(queue) - queue_idx)
        total_compute += (len(queue) - queue_idx)
        
    # 앞 -> 뒤로 옮기는 게 이득인 경우
    elif queue_idx <= len(queue) // 2:
        queue.rotate(-queue_idx)
        total_compute += queue_idx
    queue.popleft()
    
print(total_compute)
```

* deque 에 대해 공부를 좀 해두어야 다른사람의 코드를 봐도 쉽게 이해할수 있을 것 같다.
* 확실히 deque 활용으로 반복문이 줄어들었고 시간복잡도 측면에서 훨씬 우수한 결과를 가져올 것 같다.
