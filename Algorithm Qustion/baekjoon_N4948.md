# 베르트랑 공준
[백준 4948번](https://www.acmicpc.net/problem/4948) 
* 알고리즘 분류 : 에라토스테네스의 체, 소수판별
```python
from sys import stdin

def find_prime_number(n):
    prime = []
    for i in range(2, int(math.sqrt(2*n)) + 1):
        if i == 1:
            prime.append(1)
            break
        elif i < int(math.sqrt(n)):
            continue

        if i % (2*n) != 0:
            prime.append(1)
    return prime

print(find_prime_number(10))

while True:
    n = int(input())
    result = []
    find_prime_number(n, result)
    print(len(result))

    if n == 0:
        break    
        
```
> 이상하게 2n 까지의 소수가 구해지지 않았다.. 시간이 모자라서 원인규명 못하고 구글링하게됨.

## 정답코드
```python
import math

N = 123456 * 2 + 1
prime_numbers = [True] * N
for i in range(2, int(math.sqrt(N))+1):
    if prime_numbers[i]:                    # N까지의 모든 숫자들의 제곱근이 범위인데 그것들을 돌예정
        for j in range(2*i, N, i):        # N까지의 모든 i 배수들을 False 처리한다. i 는 예외
            prime_numbers[j] = False       # 에라토스테네스의 체 원리를 제대로 구현한 문장, 모든 수는 소수들의 배수이니까.. 
                                             # N까지의 제곱근 단위에 배수하면 나머지는 전부 소수가아니니
                                             
def get_prime_num_count(value):                 # 입력값의 지정된 범위안의 소수 갯수를 출력하는 함수
    count = 0
    for i in range(value + 1, (value*2) + 1):    # N보다 크고 2N 보다는 작거나 같은 소수 구하기위한 범위 설정
        if prime_numbers[i]:
            count += 1
    return count

result = []

while True:
    value = int(input())
    if value == 0:
        break
    result.append(get_prime_num_count(value))

for i in result:
    print(i)
```
* 123456 숫자범위안의 모든 소수를 먼저 구해놓고 이후 n<a<2n 범위안에 대입하여 풀었다.
* 소수 구하는 부분에서 에라토스테네스의 체 이론을 올바르게 사용한듯 하다. 배우자.
