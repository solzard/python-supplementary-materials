# Python用語解説

## 標準ライブラリ

### `range()`

```python
"""range() の使い方

range(stop) := 0,1,2,3,...,stop-1の数を返す
    range(5) -> 0,1,2,3,4
    range(10) -> 0,1,2,3,4,5,6,7,8,9

range(start, stop) := start,start+1,start+2,...,stop-1の数を返す
    range(2, 7) -> 2,3,4,5,6
    range(10, 16) -> 10,11,12,13,14

range(start, stop, step) := start,start+step,start+2*step,...,stop-step,stop-1の数を返す
    range(2, 7, 2) -> 2,4,6
    range(0, 41, 8) -> 0,8,16,24,32,40
    range(0, 15, 3) -> 0,3,6,9,12
    range(0, 16, 3) -> 0,3,6,9,12,15

stepはマイナスの数を指定することもできる
    range(30, 0, -5) -> 30,25,20,15,10,5,0
    range(50, 10, -8) -> 50,42,34,26,18,10
"""

print(range(10))  # -> range(0, 10)
print(type(range(10)))  # -> <class 'range'>

# 0,1,2,3,4を1行ごとに表示する
for i in range(5):
    print(i)

# 0,8,16,24,32,40を1行ごとに表示する
for i in range(0, 41, 8):
    print(i)
```
