# String

### 고지식한 패턴 검색 알고리즘

```python
p="is"
t="This is a book"
M=len(p)
N=len(t)

def BruteForce{p,t} :
    i=0 # t의 인덱스
    j=0 # p의 인덱스
    while j < M and i < N :
        if p[j] != t[i] :
            i=i-j
            j=-1
        i += 1
        j += 1
    if j == M :
        return i-M
    else : 
        return -1
```

최악의 경우 시간복잡도는 텍스트의 모든 위치에서 패턴을 비교해야 하므로 O(MN)이 된다. (매우 안좋음)

### 카프-라빈 알고리즘



### KMP 알고리즘

시간 복잡도 : O(M+N)

T : abcdabcd

P1: abcdabcef

P2          abcdabcef로 T와 비교

```python
def kmp(t,p) :
    N = len(t)
    M = len(p)
    lps = [0] * (M+1)
    j=0 # 일치한 갯수 == 비교할 패턴 위치
    lps[0] = -1
    for i in range(1,M) :
        lps[i] = j # p[i] 이전에 일치한 갯수
        if p[i] == p[j] :
            j += 1
        else :
            j=0
    lps[M] = j
    i = 0 # 비교할 텍스트 위치
    j = 0 # 비교할 패턴 위치
    while i < N and j <= M :
        if j == -1 or t[i] == p[i] : # 첫글자가 불일치 했거나, 일치하면
            i += 1
            j += 1
        else : # 불일치
            j = lps[j]
        if j==M : # 패턴을 찾을 경우
            print(i-M, end=' ') # 패턴의 인덱스 출력
            j = lps[j]
```

### 보이어-무어 알고리즘

끝에서부터 체크하는 알고리즘

### 호스풀 알고리즘

