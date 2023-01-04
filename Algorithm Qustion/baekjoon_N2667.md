# 단지번호 붙이기
[백준 2667번](https://www.acmicpc.net/problem/2667)
* 분류 : DFS & BFS

## 나의 풀이
```python
N = int(input())


square = [list(map(int, input())) for _ in range(N)]

count = 0

def dfs(x, y):  #시작지역이 1이면 그곳과 연결된 단지의 규모를 파악하는 함수 / 0이면 돌지 않고 끝
    global count
    if x <= -1 or x >= N or y <= -1 or y >= N:  #범위를 벗어났을 때 
        return False
    
    elif square[x][y] == 1:    #방문기록이 없을 때
        square[x][y] = 0       # 다시 만나면 탐색 안하게 0으로 바꿔놓음(방문처리)
        count += 1             # 집 갯수 카운트 업
        
        dfs(x -1, y)         # 상하좌우로 좌표 탐색
        dfs(x, y - 1)
        dfs(x + 1, y)
        dfs(x, y + 1)
        return True and count          # 확인이 끝나면 True와 만났던 1의 갯수(집)를 리턴해줌
        
    return False #0을 만났을 때 그냥 끝
    
    
tot_count = 0  # 단지의 총 개수

house_count = []  # 단지를 이루는 집들의 개수 리스트

for i in range(N):         # 마을의 좌표 하나하나를 확인하며 집이 있으면(1이라면) 
    for j in range(N):       # 그것이랑 연결된 단지의 규모를 함수를 써서 파악하는 ㅇㅇ
        if dfs(i, j):
            tot_count += 1
            house_count.append(count)
        else:
            count = 0


print(tot_count)
house_count.sort()

for i in house_count:
    print(i)
```
* 유튜브 영상으로 DFS 관련 문제풀이 영상을 참고하면서 풀기는 했지만 답지를 안보고 DFS를 정답까지 해냈다는것에 매우 만족함
* 조금은 DFS 사용방식이 이해가 될듯 말듯 하다. 아리송

- - -

<br>

## 풀기 전 접근방법
```
>>> 시작 지점을 설정하고, 상하좌우를 확인하면서 방문기록이 있는지 없는지 체크

>>> 방문기록 있으면 안드가고 없으면 들어가서 쭉쭉 나아가는 테크

>>> 그러면서 전부 다 돌았을때 True를 (마을갯수) 출력하게하면 마을 갯수를 알수잇게됨

>>> 집들의 수를 구하는것은 카운트를 하면 될꺼같긴한데 함수 안에 카운트를 세고 담는 기능을 넣어야 할듯 함
```


