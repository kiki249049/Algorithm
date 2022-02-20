# List1, List2, string 공부

```python
# 선택정렬
def Selectionsort(arr) :
    for i in range(len(arr)):
        for k in range(i+1,len(arr)) :
            if arr[i] > arr[k] :
                arr[i],arr[k] = arr[k],arr[i]
    return arr
arr=[2,52,2,5,68,6,6,4,1]
print(Selectionsort(arr))
# 카운팅정렬
def countingsort(arr) :
    count=[0]*(max(arr)+1)
    answer=[0] * len(arr)
    for i in range(len(arr)) :
        count[arr[i]] += 1
    for i in range(len(count)-1) :
        count[i+1] += count[i]
    for i in range(len(arr)):
        answer[count[arr[i]]-1] = arr[i]
        count[arr[i]] -= 1
    return answer
arr2=[2,52,2,5,68,6,6,4,1]
print(countingsort(arr2))
# 버블정렬
def bubblesort(arr) :
    for i in range(len(arr),0,-1):
        for k in range(i-1) :
            if arr[k] > arr[k+1] :
                arr[k] , arr[k+1] = arr[k+1] , arr[k]
    return arr
arr3=[2,52,2,5,68,6,6,4,1]
print(bubblesort(arr))
# 델타(사다리타기, 달팽이)
dx=[0,-1,0,1]
dy=[-1,0,1,0]
for i in range(N):
    for k in range(N) :
        for j in range(4):
            nx = x + dx[j]
            ny = y + dy[j]
# 부분집합
arr4 = [7,2,3,2,4,9]

n=len(arr4)
for i in range(1<<n) :
    box=[]
    for k in range(n):
        if i & (1<<k) :
            box.append(arr4[k])
    print(box)
# 이진탐색
def binarysearch(arr,key) :
    start=0
    end=len(arr)-1
    while start < end :
        middle = (start + end) // 2
        if arr[middle] == key :
            return True
        elif arr[middle] > key :
            end=middle-1
        else :
            start = middle+1
    return False
arr5=[1, 2, 2, 4, 5, 6, 52, 68]
print(binarysearch(arr5,52))

# atoi
def atoi(s):
    i=0
    for x in s :
        i = i*10 + ord(x)-ord("0")
    return i
# iota
def itoa(n) :
    answer=''
    if n < 0 :
        n=-n
        while True:
            answer += chr(n % 10 + ord('0'))
            if n % 10 == n:
                return "-"+answer[::-1]
            n = n // 10

    while True :
        answer += chr(n%10+ord('0'))
        if n%10 == n :
            return answer[::-1]
        n=n//10

# 문자열 찾기
def Bruteforce(p,t) :
    M=len(p)
    N=len(t)
    i=0
    j=0
    while j<M and i<N :
        if p[j] != t[i] :
            i -= j
            j = -1
        i += 1
        j += 1
    if j == M :
        return i-M
    else :
        return False
print(Bruteforce("asd","hskwosasdlskg"))
```

