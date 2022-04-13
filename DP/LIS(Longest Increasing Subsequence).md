

# LIS(Longest Increasing Subsequence)

```python
D[i] = max(D[i],D[j]+1) if array[j] < array[i]
```

```python
n=int(input())
array=list(map(int,input().split()))
array.reverse()

dp=[1]*n

for i in range(1,n) :
    for j in range(0,i) :
        if array[i] < array[j] :
            dp[i] = max(dp[i], dp[j]+1)
            
            
print(n-max(dp))
```

# dp 화폐

```python
n,m = map(int, input().split())
array=[]
for i in range(n) :
    array.append(int(input()))

d = [10001] * (m+1)

d[0]=0
for i in range(n):
    for j in range(array[i],m+1) :
        if d[j-array[i]] != 10001 :
            d[j] = min(d[j],d[j-array[i]]+1)
 
if d[m] == 10001 :
    print(-1)
else :
	print(d[m])
```

### 회의수 백준 문제

```python
arr = []
for _ in range(int(input())):
    start, end = map(int, input().split())
    arr.append((start, end))
arr.sort(key=lambda x: x[0]) # x기준으로 정렬
arr.sort(key=lambda x: x[1]) # y기준으로 정렬 # 같은 y좌표에서 x가 오름차순으로 정렬시킬려고 x기준으로도 정렬을 시켜준다.

end = cnt = 0
for t in arr:
    if t[0] >= end:
        end = t[1]
        cnt += 1
print(cnt)
```

