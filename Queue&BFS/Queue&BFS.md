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
        if not visited[t] :
            visited[t] = 1
        print(f'정점노드:{t} 방문상태:{visited}')
        print(f'큐상태:{queue}')
        for i in range(1,len(G[t])) :
            if not visited[i] and G[t][i]==1 :
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



