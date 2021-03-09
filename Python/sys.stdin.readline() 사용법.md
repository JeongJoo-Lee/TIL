 # sys.stdin.readline()
 ## input() 대신 sys.stdin.readline()을 사용하는 이유
 * 여러 줄 입력 받아야 할 경우 input()은 시간초과가 발생 할 수 있기 때문이다.
 
 
 ## 사용법
 ### 한개의 정수를 입력 받을 때
 ```python
 import sys
 num = int(sys.stdin.readline())
 ```
 **int()를 씌워 준 이유**
 > sys.stdin.readline()은 한줄 단위로 입력받기 때문에, 개행문자가 같이 입력 받아짐
 > 만약 3을 입력 했다면, 3|n 이 저장되기 때문에 개행문자를 제거해야한다.
 > 또한 변수타입이 **문자열 형태(str)** 로 저장되기 때문에, 정수로 사용하기 위해서 int() 형변환을 거쳐야 한다.
  
 - - -
 
 ### 정해진 개수의 정수를 한줄에 입력 받을 때
 ```python
 import sys
 a,b,c = map(int,sys.stdin.readline().split())
 ```
 > map()은 반복 가능한 객체(리스트 등)에 대해 각각의 요소들을 지정된 함수로 처리해 주는 함수, 활용하기
  
 - - -
 
 ### 임의의 개수의 정수를 한줄에 입력받아 리스트에 저장할 때
 ```python
 import sys
 data = list(map(int, sys.stdin.readline().split()))
 ```
 > split() 을 넣어주면 공백(space,tab,enter)을 기준으로 나눈다.
  
 - - -
 
 ### 임의의 개수의 정수를 n줄 입력받아 리스트에 저장할 때
 ```python
import sys
n = int(sys.stdin.readline())
data = [sys.stdin.readline().strip() for i in range(n)]
```
> 문자열의 공백을 제거해주는 strip()과 활용해서 저장


내용 출처 : [yeseolee.log](https://velog.io/@yeseolee/Python-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9E%85%EB%A0%A5-%EC%A0%95%EB%A6%ACsys.stdin.readline)
 
