# 분해합
[백준 2231번](https://www.acmicpc.net/problem/2231)
* 분류 : 브루트포스 알고리즘
- - -

## 나의 풀이
```python
N = int(input())

target = 0
result = []

i = 0

while i <= N:
    i += 1

    if i < 10:
        target = i + i
    elif i < 100:   #십의자리수
        target = i + (i//10) + (i % 10)
    elif i < 1000:  #백의자리수
        target = i + (i // 100) + (i % 100 // 10) + (i % 100 % 10)
    elif i < 10000:  #천의자리수
        target = i + (i // 1000) + (i % 1000 // 100) + (i % 1000 % 100 //10) + (i % 1000 % 100 % 10)
    elif i < 100000:  #만의 자리수
        target = i + (i // 10000) + (i % 10000 //1000) + (i % 10000 % 1000 //100) + (i % 10000 % 1000 % 100 //10) + (i % 10000 % 1000 % 100 % 10)
    elif i < 1000000:  #십만의 자리수
        target = i + (i//100000) + (i % 100000 //10000) + (i % 100000 % 10000 //1000) + (i % 100000 % 10000 % 1000 //100) + (i % 100000 % 10000 % 1000 % 100 //10) + (i % 100000 % 10000 % 1000 % 100 % 10)
    else:
        target = 10000001
    
    if target == N:
        result.append(i)
    
if not result:              #생성자가 없을경우에 0을 출력한다. 라는 조건을 안넣어서 런타임 에러 발생함!!
    print(0)
else:
    print(min(result))
```
> 너무 무식하게 풀었다. 정답은 맞았지만 코드가 간결하지 못하다.
<br><br>

- - -

## 다른사람 풀이
```python
N = int(input())
result = 0

for i in range(1, N+1):

    # str 함수를 통해 i의 각 자리수를 A리스트에 넣는다.
    A = list(map(int, str(i)))
    
    # 각 자리수의 합인 sum(A)와 i 본연의 값을 더한 최종값을 result 변수에 넣는다.
    result = i + sum(A)

    # N의 값이 되면 출력하고 반복문 종료
    if result == N:
        print(i)
        break

    # result 값은 i 보다 무조건 크기 마련인데 그때까지 break가 안되고 i가 N 값까지 도달했다는 뜻은 생성자(result)가 없었다는 뜻. 이때는 0출력하고 마무리
    if i == N:
        print(0)
```
> 문자열로 바꿔서 자리수를 쪼개고 다시 정수로 돌아와 계산하였다. 이런 접근법 숙지해두자
