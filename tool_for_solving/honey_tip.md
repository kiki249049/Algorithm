### key 값으로 정렬시키는 방법

```python
a.sort(key=lambda x : len(x))
```

이처럼 lambda함수를 써서 안에 있는 원소를 기준으로 정렬시킬 수 있다.

### 부분집합

```python
arr=[3,1,2,5,4]
n=len(arr)
for i in range(1<<n) :
    for k in range(n) :
        if i & (1<<k) :
            print(arr[k])
```

### 순열

```python
def permutation(arr,n) :
    result = []
    if n == 0 :
        return [[]]
    for i,elem in enumerate(arr) :
        for p in permutation(arr[:i]+arr[i+1:],n-1) :
            result += [[elem]+p]
    
    return result
```

### 인풋값 숫자만 int로 바꾸기

```python
def int_chg(char) :
    if char.isdecimal() :
        return int(char)
    else :
        return char
```

