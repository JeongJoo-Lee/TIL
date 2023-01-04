# 소수구하기
[백준 1929번](https://www.acmicpc.net/problem/1929)

## 처음 제출한 오답
```python
A, B = map(int, input().split())

def find_prime_number(target_num):      #소수 판별 함수  / 잘보면 입력값(target_num)이 1일때의 경우가 빠져있다.
    for i in range(2, target_num):      #가장 큰 문제점 : 범위를 제곱근으로 축소하지 않는바람에 시간복잡도가 최대치를 찍고 폭주해버렸다.
        if target_num % i == 0:
            return False
    return True

for num in range(A, B+1):
    if find_prime_number(num) == True:
        print(num)
```
* **소수의 성질**과 **에라토스테네스의 체**에 대해 잘 모르고 무작정 달려든 것이 패인이었다.
> 소수 : 1과 본인을 제외한 숫자로는 나누어지지 않는 수
> 소수는 N의 제곱근 보다 크지 않은 어떤 소수로도 나눠지지 않는다.
> 에라토스테네스의 체 : 모든 자연수는 소수들의 곱으로 표현이 되며, 정해진 범위가 있다면 2부터 시작해서 배수로 소수 명단에서 제거해 나가는 방식

- - -
## 이후 제출한 정답
```python
A, B = map(int, input().split())

def find_prime_number(target_num):
    if target_num == 1:
        return False
    for i in range(2, int(target_num**0.5)+1):     # +1 해준이유 : 제곱근이 2인 숫자들의 경우 range(2, 2) 가되어 반복이 성립되지 않음     
        if target_num % i == 0:                           
            return False                                  
    return True

for num in range(A, B+1):
    if find_prime_number(num):
        print(num)
```
* 소수는 해당값의 제곱근보다 크지 않은 어떤 소수로도 나눠지지 않는다. 라는 특징을 이용한 제곱근 범위 감소로 시간복잡도를 줄임으로서 시간초과 문제를 해결
* 소수 판별 함수에서 입력값(target_num)이 1일때를 다시 넣어줌으로서 오답 해결

        
