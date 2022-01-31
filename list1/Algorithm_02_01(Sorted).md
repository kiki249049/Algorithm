# Algorithm(SWEA)

### 1. List1

1. 슈도코드

일반적인 언어로 코드를 흉내내어 알고리즘을 써놓은 코드

![image-20220131234049801](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234049801.png)

2. 순서도

![image-20220131234115117](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234115117.png)

### 무엇이 좋은 알고리즘인가?

![image-20220131234232880](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234232880.png)

정확성, 작업량, 단순성, 메모리사용량, 최적성

![image-20220131234339504](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234339504.png)

더하려는 범위가 클수록 연산횟수의 차이가 커짐

### 시간복잡도

![image-20220131234533039](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234533039.png)

실행되는 명령문의  수를 계산

### 빅-오표기법

![image-20220131234609992](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234609992.png)

![image-20220131234641827](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131234641827.png)

![image-20220131235254380](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131235254380.png)

![image-20220131235716657](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131235716657.png)

![image-20220131235739761](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220131235739761.png)

## Exhaustive Search

![image-20220201000152377](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201000152377.png)

![image-20220201000851036](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201000851036.png)

**중요!!**

## Greedy Algorithm

탐욕알고리즘

![image-20220201001049354](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201001049354.png)

![image-20220201001240424](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201001240424.png)

![image-20220201001401742](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201001401742.png)

![image-20220201001508475](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201001508475.png)

![image-20220201001715508](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201001715508.png)

## Sort

![image-20220201002008408](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002008408.png)

![image-20220201002050955](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002050955.png)

-> 매우 비효율적인 알고리즘 O(n**2)

![image-20220201002133585](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002133585.png)

![image-20220201002241910](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002241910.png)

```python
def BubbleSort(a) :
    for i in range(len(a)-1,0,-1) :
        for j in range(0,i) :
            if a[j] > a[j+1] :
                a[j],a[j+1] = a[j+1],a[j]
```

![image-20220201002437809](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002437809.png)

![image-20220201002654740](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002654740.png)

![image-20220201002759661](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002759661.png)

![image-20220201002850068](C:\Users\kiki2\AppData\Roaming\Typora\typora-user-images\image-20220201002850068.png)

```python
# A=[0,1,1,2,3,2,4,1,2]
def countingsort(A,B) :  # A는 날것의 data B는 정답데이터 C는 카운팅데이터
    C=[0]*(max(A)+1)
    for i in A:
        C[i] += 1 # 카운트리스트 C완성

    for i in range(1,len(C)) :
        C[i] += C[i-1]  # 앞에있는 카운트리스트를 계속 더함

    for i in range(len(A)-1, -1 ,-1) :
        B[C[A[i]-1]] = A[i]   # B에 정렬시키고
        C[A[i]] -= 1		# 정렬시킨 A의 원소의 카운트를 1깎는다.
              
```

