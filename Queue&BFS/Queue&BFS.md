# Queue

```python
def enqueue(item) :
    global rear
    if rear == len(queue)-1 : print("queue_full")
    else :
        rear += 1
        queue[rear] = item
def dequeue() :
    global front
    if front == rear :
        print("queue empty")
    else :
        front += 1
        return queue[front]
def qpeek() :
    if rear == front :
        print("queue empty")
    else :
        return queue[front+1]
queue=[0]*3
front = -1
rear = -1
enqueue(1)
enqueue(2)
enqueue(3)
print(queue)
for i in range(len(queue)) :
    print(dequeue())
```

# BFS

```python
from pprint import pprint
def BFS(G,v,visited) :
    queue=[]
    queue.append(v)
    while queue :
        t=queue.pop(0)
        print(f'정점노드:{t} 방문상태:{visited}')
        print(f'큐상태:{queue}')
        for i in range(1,len(G[t])) :
            if not visited[i] and G[t][i]==1 :
                visited[i] = 1
                queue.append(i)

V,E=map(int,input().split())
connect = list(map(int,input().split()))
G=[[0]*(V+1) for _ in range(V+1)]
visited = [0] * (V + 1)
for i in range(E) :
    G[connect[2*i]][connect[2*i+1]] = 1
    G[connect[2*i+1]][connect[2*i]] = 1
pprint(G)
BFS(G,1,visited)
```

# 최소 경로 BFS

```python
def bfs(x,y,N) :
    visited=[[0]*N for _ in range(N)] # 미로의 크기만큼 visited 생성
    queue=[]        # 큐 생성
    queue.append([x,y])  # 시작점 인큐
    visited[x][y] = 1  # 시작점 방문표시
    while queue :  # 큐가 비어있지 않으면 반복
        x,y=queue.pop(0) # 디큐
        if maze[x][y] == 3 :
            return visited[x][y] - 2 # 출발과 도착을 뺀 칸의 수
        for dx,dy in [[1,0],[0,-1],[-1,0],[0,1]] :
            nx,ny = x+dx, y+dy # 주변 칸 좌표
            if 0<=nx<N and 0<=ny<N and  maze[nx][ny] != 1 and visited[nx][ny] == 0 :
                queue.append([nx,ny])
                visited[nx][ny] = visited[x][y] + 1
    return 0

T = int(input())
for tc in range(1,T+1) :
    N=int(input())
    maze=[list(map(int,input())) for _ in range(N)]
    for i in range(N) :
        for k in range(N) :
            if maze[i][k] == 2:   # 시작점 찾기
                x,y=i,k
                break
    ans = bfs(x,y,N)
    print(f'#{tc} {ans}')
```



