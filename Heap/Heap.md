## 최소 힙

힙은 항상 O(logn)의 시간복잡도를 유지한다.

insert

```python
heap = [0,2,3,5,4,7,6] # 앞의 0은 인덱스 맞춰줄려고 일부러 형식적으로 넣어준것.

import sys
input = sys.stdin.readline
def Insert(num) :
  # 1. 제일 마지막 단말 노드에 데이터를 삽입한다.
  heap.append(num)
  numIdx = len(heap)-1
  # 2. 부모 노드랑 계속 비교하면서 부모 노드가 자신보다 크다면 부모와 자신의 위치를 swap
  # 3. 2번 조건을 만족하지 않을 때까지 또는 자신이 루트 노드가 아닐 때까지 반복한다.
  while ((numIdx != 1) and (num < heap[numIdx//2])) :
    heap[numIdx], heap[numIdx//2] = heap[numIdx//2], heap[numIdx]
    numIdx = numIdx // 2

Insert(1)

# 출력 결과
[0, 2, 3, 1, 4, 7, 6, 5]
[0, 1, 3, 2, 4, 7, 6, 5]
```

delete

```python
heap = [0, 1, 3, 2, 4, 7, 6, 5] # 이것도 앞의 0은 인덱스 맞출려고 넣어준거라 무시.

def Delete(heap) :
  # 1. 가져올 '최소값'을 미리 저장해준다.
  result = heap[1]
  # 2. 가장 마지막 노드의 값과 루트 노드의 값을 Swap 해준다.
  heap[-1], heap[1] = heap[1], heap[-1]
  # 삭제할 값을 맨 뒤로 보냈으니, 삭제해준다.
  heap.pop()

  # 3. 현재 노드에서 자식 노드와 비교 하면서 자식 노드가 더 작은 값이라면 Swap해준다.
  # 4. 위치를 찾을 때 까지 3번 과정을 반복한다.
  parent = 1
  while (True) :
    child = parent * 2

    if (child+1 < len(heap) and heap[child] > heap[child+1]) : child += 1
    if (child >= len(heap) or heap[child] > heap[parent]) : break
    heap[child], heap[parent] = heap[parent], heap[child]
    parent = child
  print(result,heap)

Delete(heap)
```

### import heapq

heappush() : 힙에 원소를 넣는 명령어

```python
heapq.heappush(heap,4)
heapq.heappush(heap,1)
heapq.heappush(heap,7)
heapq.heappush(heap,3)
heap=[1, 3, 7, 4]
```

heappop() : 힙에 맨 위의 노드를 삭제하는 명령어(쉽게 말해 최솟값을 삭제)

```python
print(heapq.heappop(heap))
print(heap)
1
[3, 4, 7]
```

삭제하는 메커니즘 : 맨 위의 노드와 맨 끝의 노드를 바꾼다. 그리고 맨 위의 노드를 자식노드와 비교하면서 본인이 더 크면 아래로 내려가는 하향식으로 다시 배열하는 식이다.

### 기존 리스트를 힙으로 변환

```python
heap = [4, 1, 7, 3, 8, 5]
heapq.heapify(heap)
print(heap)

[1, 3, 5, 4, 8, 7]
```

### 최소힙을 최대힙으로 만드는 법

`heapq` 모듈은 최소 힙(min heap)을 기능만을 동작하기 때문에 최대 힙(max heap)으로 활용하려면 약간의 요령이 필요합니다. 바로 힙에 튜플(tuple)를 원소로 추가하거나 삭제하면, 튜플 내에서 맨 앞에 있는 값을 기준으로 최소 힙이 구성되는 원리를 이용하는 것입니다.

따라서, 최대 힙을 만들려면 각 값에 대한 우선 순위를 구한 후, `(우선 순위, 값)` 구조의 튜플(tuple)을 힙에 추가하거나 삭제하면 됩니다. 그리고 힙에서 값을 읽어올 때는 각 튜플에서 인덱스 1에 있는 값을 취하면 됩니다. (우선 순위에는 관심이 없으므로 )

```python
import heapq

nums = [4, 1, 7, 3, 8, 5]
heap = []

for num in nums:
  heapq.heappush(heap, (-num, num))  # (우선 순위, 값)

while heap:
  print(heapq.heappop(heap)[1])  # index 1
```

### K번째 최솟값/최댓값

```python
import heapq

def kth_smallest(nums, k):
  heap = []
  for num in nums:
    heapq.heappush(heap, num)

  kth_min = None
  for _ in range(k):
    kth_min = heapq.heappop(heap)
  return kth_min

print(kth_smallest([4, 1, 7, 3, 8, 5], 3))

4
```

### 힙 정렬

```python
import heapq

def heap_sort(nums):
  heap = []
  for num in nums:
    heapq.heappush(heap, num)

  sorted_nums = []
  while heap:
    sorted_nums.append(heapq.heappop(heap))
  return sorted_nums

print(heap_sort([4, 1, 7, 3, 8, 5]))

[1, 3, 4, 5, 7, 8]
```

제일 위자리는 가장 작은수가 나오는 힙의 특성을 이용한 정렬 logN의 시간복잡도를 N번 수행하니 시간복잡도는 NlogN이다
