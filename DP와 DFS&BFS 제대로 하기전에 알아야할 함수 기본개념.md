# DP와 DFS&BFS 제대로 하기전에 알아야할 함수 기본개념

```python
immutable = 1
mutable = [1, 2, 3]

def func1():
    mutable[0] = 1
    # indexing을 통한 변경. 재할당 x
    # global 변수 mutable만을 변경함.
    # local 변수 선언 x

def func2(mutable):
    mutable[0] = 1
    # global 변수 mutable 넘겨줄 경우
    # local과 global이 둘다 동일한 객체를 가리키므로,
    # 두 변수 모두 수정됨.
func2(mutable)

def func3():
    mutable = [7, 7, 7]
    # global 변수 수정 x
    # 새로운 local 변수 mutable 생성함.
    # global 변수에 재할당을 위해서는 global 키워드 사용해야함
```

```


```

