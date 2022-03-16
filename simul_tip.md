```python
def hit(hit) :
    global out,score,b1,b2,b3
    player = [0]
    if hit == 1 :
        score += b3
        b1,b2,b3 = 1,b1,b2
    elif hit == 2 :
        score += (b2+b3)
        b1,b2,b3 = 0,1,b1
    elif hit == 3 :
        score += (b1+b2+b3)
        b1,b2,b3 = 0,0,1
    else :
        score += (b1+b2+b3+1)
        b1,b2,b3 = 0,0,0
    return

```

포문으로 일일히 안돌리고 base 한칸씩 옮기게하는법