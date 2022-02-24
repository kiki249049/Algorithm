# DFS

```python
def dfs(v) :
    global visited
    stack = [v]
    while stack:
        v = stack.pop()
        if not visited[v] :
            visited[v] = 1
            print(f'방문 정점:{v}, 방문 체크 :{visited}')
            for j in range(1,V+1) :
                if G[v][j] == 1 and not visited[j] :
                    stack.append(j)

V,E = map(int,input().split())
temp = list(map(int,input().split()))
G=[[0]*(V+1) for _ in range(V+1)]
visited=[0]*(V+1)

for i in range(E) :
    G[temp[i*2]][temp[i*2+1]] = 1
    G[temp[i * 2+1]][temp[i*2]] =1
pprint(G)

dfs(1)
```

```python
def f(i,N,s,t) : # s 이전까지 고려된 원소의 합, t 목표값
    global cnt
    cnt += 1
    if s==t : #목표값을 찾으면
        for j in range(N) :
            if bit[j] == 1 :
                print(a[j], end=' ')
        print()
    elif i==N : # 더이상 고려할 원소가 없으면
        return
    elif s > t : # 합이 고려한 원소보다 높다
        return
    else :
        bit[i] = 1
        f(i+1, N, s+a[i], t)
        bit[i] = 0
        f(i+1, N, s, t)
    return
a = [1,2,3,4,5,6,7,8]
cnt =0
bit = [0]*len(a)
print(f(0,len(a),0,8))
print(cnt)
```

