# 🥇두개의 리스트 내부 각 요소들 끼리의 합 구하기

## 🥈for문과 zip()함수 활용
```python
a = [1, 2, 3, 4, 5]
b = [10, 20, 30, 40, 50]

c = [x + y for x, y in zip(a, b)]

print(c)

>>> [11, 22, 33, 44, 55]
```

## 🥉for문과 index 활용
```python
c = [ a[i] + b[i] for i in range(len(a))]

print(c)

>>> [11, 22, 33, 44, 55]
```
