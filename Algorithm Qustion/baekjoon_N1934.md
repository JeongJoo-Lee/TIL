# 최소공배수
[백준 1934번](https://www.acmicpc.net/problem/1934)
* 분류 : 정수론, 유클리드 호제법
```python
def greatest_common_factor (a, b):    #유클리드 호제법
    if a < b:
        (a, b) = (b, a)
    while b != 0:
        (a, b) = (b, a % b)
    return a

result = []

T = int(input())
for i in range(T):
    A, B = map(int, input().split())
    GCF = greatest_common_factor(A, B)
    LCM = (A//GCF)*(B//GCF)*GCF
    result.append(LCM)

for i in result:
    print(i)
```
![image](https://user-images.githubusercontent.com/61656046/111157476-42804780-85da-11eb-951f-973b3706779b.png)

* 유클리드 호제법이 아직 잘 이해가 되지 않는다. 계속 봐야겠다.
