### 딕셔너리를 이용한 hash풀이(시간 매우 절약가능)

```python
import sys
from copy import deepcopy
input = sys.stdin.readline

N=int(input())
nums=list(map(int,input().split()))
store=deepcopy(nums)
ans = [0]*N
temp={}
nums=set(nums)
nums=sorted(nums)
for i in range(len(nums)) :
    temp[nums[i]] = i
for i in range(N) :
    if store[i] in temp :
        print(temp[store[i]], end=' ')
```

순서가 아닌 in 함수를 통해 여기있냐고 찾을때는 set이나 dict을 이용하면 매우 빨리 시간복잡도 O(1)으로 원소를 찾을수있다. 

```python
max_key = max(dict, key=dict.get) # value가 최댓값인 key찾기
max_key = [k for k,v in items(dict) if v == max(dict.values())] # 위와 동일
```

