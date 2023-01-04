# 124나라의 숫자
[프로그래머스 124나라의 숫자](https://programmers.co.kr/learn/courses/30/lessons/12899)
* 연습문제 : level2(javascript)

## 나의 풀이
```javascript
function solution(n) {
    var answer = '';
    var spareNum = '';
    
    while(n > 0){
        spareNum = n % 3;
        n = Math.floor(n / 3);
        if (spareNum == 0) {
            n -= 1;
            spareNum = 4;
        }
        answer = spareNum + answer;    
        
    }    
    return answer;
}
```
## 배운점
### javascript Math.floor 메소드 활용법
* Math.floor() 함수는 주어진 숫자와 같거나 작은 정수 중에서 가장 큰 수를 반환합니다.
```
// 예제
Math.floor( 45.95); //  45
Math.floor( 45.05); //  45
Math.floor(  4   ); //   4
Math.floor(-45.05); // -46
Math.floor(-45.95); // -46
```
