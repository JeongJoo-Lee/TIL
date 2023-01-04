# Fly me to the Alpha Centauri
[백준 1011번](https://www.acmicpc.net/problem/1011)
## 정답 코드
```python
import math

N = int(input())

count = 0                                    #최소 작동 횟수
result = []

for _ in range(N):
    a, b = map(int, input().split())
    distance = b - a                         #주어진 값들간의 거리

    num = math.floor(math.sqrt(distance))             #주어진 값들 사이의 거리에 루트 씌움 (제곱근) , floor처리되어 이미 정수임
    num_jegob = num**2                            # 정수를 제곱근으로 갖는 제곱수(ex. 9 : 9의 제곱근은 3)

    if distance == num_jegob:
        count = (num*2)-1

    elif num_jegob < distance <= num_jegob + num:
        count = (num*2)

    elif (num_jegob + num) < distance:
        count = (num*2) + 1

    elif distance < 4:
        count = distance
    result.append(count)



for x in result:
    print(x)
```
* 문제 이해하는것부터 쉽지 않았던 문제... 패턴찾기도 생각보다 어렵다.
* 이 문제해설을 통해 제곱근과 제곱수의 개념에 대해 제대로 알게되었다.
* 자세한 내용은 [블로그](https://data-jj.tistory.com/36)에 포스팅하였음

```python
math.floor # 내림 기능 3.xxxxx 전부 3으로 만들 수 있음 int로 해줘도 되긴함 근데 새로운거 쓰면서 배우는게 더 좋으니까
```


