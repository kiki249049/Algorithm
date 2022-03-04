# Memorization

```python
import sys
input=sys.stdin.readline

def cnt_0(n) :
    global cnt
    cnt += 1
    if n <= 1:
        return cnt0[n]
    elif not cnt0[n]:
        cnt0[n] = cnt_0(n - 1) + cnt_0(n - 2)
        return cnt0[n]
    else:
        return cnt0[n]

def cnt_1(n) :
    if n<=1 :
        return cnt1[n]
    elif not cnt1[n] :
        cnt1[n]=cnt_1(n-1)+cnt_1(n-2)
        return cnt1[n]
    else :
        return cnt1[n]


T=int(input())
for tc in range(T) :
    cnt =0
    n=int(input())
    cnt0=[0]*101
    cnt0[0]=1
    cnt0[1]=0
    cnt1=[0]*101
    cnt1[0]=0
    cnt1[1]=1
    print(cnt_0(n),end=' ')
    print(cnt_1(n))
    print(cnt)

```

