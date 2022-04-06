# N-queens 룩업테이블을 이용한 풀이

```python
def dfs(n) :
    global ans
    if n == N :
        ans += 1
        return

    for j in range(N) :
        if v1[j] == v2[n+j] == v3[n-j]==0 :
            v1[j] = v2[n+j] = v3[n-j] = 1
            dfs(n+1)
            v1[j] = v2[n + j] = v3[n - j] = 0


N = int(input())
ans = 0
# 룩업테이블
# 열 ,오른위 대각, 왼쪽아래 대각
v1, v2, v3 = [0]*30, [0]*30, [0]*30
dfs(0)
print(ans)
```

오른위 대각은 합을 이용한것으로 인덱스를 정하고

왼쪽 아래대각은 차를 이용한것으로 인덱스를 정한다.