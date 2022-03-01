# Circular Queue

```python
circular_queue=[]
front=0
rear=0
rear=(rear+1)%len(circular_queue) # 다음 삽입위치 rear
front=(front+1)%len(circular_queue) # 다음 삽임위치 front

def isempty() :
    return front == rear
def isfull() :
    return (rear+1)%len(circular_queue) == front
def enqueue(item) :
    global rear
    if isfull() :
        print('queue_full')
    else :
        rear = (rear+1)%len(circular_queue)
        circular_queue[rear] = item
def dequeue():
    global front
    if isempty():
        print('queue_empty')
    else :
        front = (front+1)%len(circular_queue)
        return circular_queue[front]
def c(a) :
    return a+b
```

