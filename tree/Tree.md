# Tree

input : 

```python
13 #V 노드 수
1 2 1 3 2 4 3 5 3 6 4 7 5 8 5 9 6 10 6 11 7 12 11 13
```

### Tree에 노드를 받는것 구현

```python
V=int(input())
connect=list(map(int,input().split()))
ch1=[0]*(V+1)
ch2=[0]*(V+1)
for i in range(V-1) :
    p,c = connect[2*i],connect[2*i+1]
    if not ch1[p] :
        ch1[p] = c
    else :
        ch2[p] = c
```

### pre,in,post 순회

```python
def pre_order(n) :
    if n : # n 에 0이 들어올경우는 안됨
        print(n)
        pre(ch1[n])
        pre(ch2[n])
        
def in_order(n) :
    if n : # n 에 0이 들어올경우는 안됨
        in_order(ch1[n])
        print(n)
        in_order(ch2[n])
        
def post_order(n) :
    if n : # n 에 0이 들어올경우는 안됨
        post_order(ch1[n])
        post_order(ch2[n])
        print(n)
```

### root 찾기

```python
# 먼저 역함수처럼 자식기준으로 부모노드를 찾아야함.
V=int(input())
connect=list(map(int,input().split()))
par=[0]*(V+1)
for i in range(V-1) :
    p,c = connect[2*i], connect[2*i+1]
    par[c]=p
# root 찾기
root = 0 
for i in range(1,V+1) :
    if par[i] == 0 : # 부모가 없는애가 root
        root = i 
# 조상찾기
c = int(input())
anc = []
while par[c] :
    anc.append(par[c])
    c=par[c]
print(anc)    
```

### 최소힙 삽입

```python
tree = [0,1,2,3,5,9,6,7]

def enq(n) :
    tree.append(n)
    idx = len(tree)-1
    while idx >= 1 and tree[parent] > tree[child] :
        parent = idx//2
        tree[parent],tree[child] = tree[child], tree[parent]
        idx = parent

def del() :
    tree[1],tree[-1] = tree[-1], tree[1]
    tree.pop()
    parent=1
    while True : 
        child = parent * 2
    	if child+1 < len(tree) and tree[child] > tree[child+1] :
        child += 1
      	if child >= len(tree) or tree[child] > tree[parent] :
            break
        tree[child],tree[parent]=tree[parent],tree[child]
        parent = child
    
```

