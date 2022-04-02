# MST

MST - 그래프에서 **모든 노드를 포함**하면서 **사이클이 존재하지 않는** 부분그래프

### union, find_parents

```python
# 최소신장트리 MST
def find_parent(parent,x) : # 특정 원소가 속한 집합을 찾기
    # 루트 노드를 찾을때까지 재귀 호출
    if parent[x] != x :
        parent[x] = find_parent(parent,parent[x])
    return parent[x]

def union_parent(parent,a,b) :
    a = find_parent(parent,a)
    b = find_parent(parent,b)
    if a < b :
        parent[b] = a
    else :
        parent[a] = b

v,e = map(int,input().split())
parent = [0] * (v+1) # 부모테이블 초기화
for i in range(1,v+1) :
    parent[i] = i
for i in range(e) :
    a, b = map(int, input().split())
    union_parent(parent,a,b)

print(f'각 원소가 속한 집합: ',end=' ')
for i in range(1,v+1) :
    print(find_parent(parent,i), end=' ')
print()
# 부모테이블
print(f'부모테이블 : {parent}')
```

