# DFS와 BFS
[백준 1260번](https://www.acmicpc.net/problem/1260)
* 분류 : DFS, BFS
## 나의 풀이
```python
from sys import stdin

N, M, V = map(int, stdin.readline().split())

graph = {}

for i in range(N):
    graph[i+1] = []


for i in range(M):
    a, b = map(int,stdin.readline().split())

    graph[a].append(b)
    graph[b].append(a)
    

def dfs(graph, start_node):
    stack = [start_node]
    visited = []        
    if start_node not in graph:
        visited.append(n)
        return

    while stack:
        current_node = stack.pop()
        visited.append(current_node)
        for num in graph[current_node]:
            if num not in visited:
                stack.append(num)
                                         
    return visited                       
                                         

def bfs(graph, start_node):
    queue = [start_node]
    visited = []
    while queue:
        current_node = queue.pop(0)
        visited.append(current_node)
        for num in sorted(graph[current_node]):
            if num not in visited and num not in queue:
                queue.append(num)
    return visited



print(dfs(graph, V), bfs(graph, V), sep='\n')
```
> 간선이 0일때 조건을 추가하고, visited 에 추가되어 작동해야되는 값들이 무분별하게 정렬되지않고 들어가서 깊이 들어가는 순서가 꼬이고 실패함
>> 어떻게 고쳐야 할지는 알겠지만 거의 마무리단계에서 삐긋한 코드를 잘못된 부분만 지엽적으로 고친다는게 말처럼 쉽지않았고 결국 실패.

- - -
## 정답


```python
N,M,V=map(int,input().split())
matrix=[[0]*(N+1) for i in range(N+1)]


for i in range(M):
    a,b = map(int,input().split())
    #간선이 연결된 것들을 1로 표시, [a][b]=[b][a]=1 해주는 이유는 1 - 4 는 1은 4와 연결되어있고 4는 1과 연결되어있다. 로 볼수있기때문!
    matrix[a][b]=matrix[b][a]=1               
visit_list=[0]*(N+1)

def dfs(V):
    visit_list[V]=1 #방문한 점 1로 표시
    print(V, end=' ') # 방문 순서대로 입력이 되겠지
    #i 노드가 어디랑 연결되어있는지 확인
    for i in range(1,N+1):
        # 만약 방문한적이없고, 연결이 되어있으면 재귀(현재 방문해있는 i 로 새로시작)
        if(visit_list[i]==0 and matrix[V][i]==1):
            dfs(i)

def bfs(V):
    queue=[V] #들려야 할 정점 저장(시작점)
    visit_list[V]=0 #방문한 점 0으로 표시
    while queue:
        V=queue.pop(0)
        print(V, end=' ') #방문한 순서대로 출력
        # 노드가 어디랑 간선연결되어있는지 확인
        for i in range(1, N+1):

            if(visit_list[i]==1 and matrix[V][i]==1):
                queue.append(i)
                visit_list[i]=0


dfs(V)
print()
bfs(V)
```
> 2차원 리스트를 활용하여 앞서 내가 신경쓰지 못했던 방문 기록에 스택 쌓는 부분을 건너뛰어 문제를 해결함
>> bfs에서 왜 방문한 점을 0으로 표시한건지는 아직도 의문인 풀이임.
