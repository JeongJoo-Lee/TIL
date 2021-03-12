# ACM 호텔
[백준 10250번](https://www.acmicpc.net/problem/10250)

## 처음 제출한 오답
```python
C = int(input())


for i in range(C):
   H, W, N = map(int, input().split())

   if N%H == 0:
       if (N//H) + 1 <10:
           print(str(N//H) + '0' + str((N//H) + 1))
       else:
           print(str(N//H) + str((N//H)+1))
   else:
       if (N//H) + 1 < 10:
           print(str(N % H) + '0' + str((N//H) + 1))
       else:
           print(str(N % H) + str((N//H) + 1))
```
 * 정수로 접근하면 될 것을 (예시 : 301 호 -> 300 + 1 호) 문자열로 접근하는 바람에 꼬였다. 생각의 폭을 좀 넓힐 필요가 있다.
- - -

## 이후 제출한 정답 
```python
C = int(input())                              # C : 터미널 수

for i in range(C):
    H, W, N = map(int, input().split())        # H : 층 , W : 너비, N : 손님의 순번

    h = N%H
    w = N//H + 1
    if h == 0:
        h = H                          
        w -= 1
        
    print(h*100 + w)
```
### 깨달은 부분
* 비교연산자(==) vs 할당연산자(=)
  * 비교연산자(==)
    * 왼쪽 피연산자와 오른쪽 피연산자의 값이 같으면 참을 반환함.(True, False)
  * 할당연산자(=)
    * 할당연산자(=)는 우측의 피연산자를 좌항의 피연산자에 할당한다. 우측 함수를 왼쪽이름으로 부르고싶을때 사용한다.
- - -
정말 기초적인 부분인데 헷갈려서 정답을 거의 다 맞췄음에도 마지막에 오류가나서 계속 헤맸다. 앞으로 다시는 안헷갈릴 짜릿한 경험이었다.
        
    
