### deepcopy는 엄청느림 되도록 [:]으로 깊은복사를 할것.

```python
virtual = [item[:] for item in area]
```

### 2차원 리스트 딥카피

```python
import sys
from collections import deque
input = sys.stdin.readline

def bfs(n) :
    queue = deque()
    z,x,y = n
    field[z][x][y] = 1 # 시작점 1
    queue.append(n)
    while queue :
        t = queue.popleft()
        z,x,y = t
        for dx,dy in [(-1,0),(1,0),(0,-1),(0,1)] :
            z,nx,ny = z,x+dx,y+dy
            if z == 0 :
                if 0<=nx<N and 0<=ny<M and not field[0][nx][ny] :
                    field[0][nx][ny] = field[0][x][y] + 1
                    queue.append((0,nx,ny))
                elif 0<=nx<N and 0<=ny<M and field[0][nx][ny] : # 점프
                    field[1][nx][ny] = field[0][x][y] + 1
                    queue.append((1,nx,ny))
            elif z == 1:
                if 0 <= nx < N and 0 <= ny < M and not field[1][nx][ny] : 
                    field[1][nx][ny] = field[1][x][y] + 1
                    queue.append((1,nx,ny))



N,M = map(int,input().split())
area = [list(map(int,input().rstrip())) for _ in range(N)]
area2 = [item[:] for item in area]
field = [area,area2]
bfs((0,0,0))
if field[0][N-1][M-1] == 0 and field[1][N-1][M-1] == 0 :
    print(-1)
elif field[1][N-1][M-1] == 0  :
    print(field[0][N-1][M-1])
elif field[0][N-1][M-1] == 0:
    print(field[1][N-1][M-1])
else :
    print(min(field[0][N-1][M-1],field[1][N-1][M-1]))
```

벽부수는 문제  3차원으로 점프하는 아이디어도 생각!