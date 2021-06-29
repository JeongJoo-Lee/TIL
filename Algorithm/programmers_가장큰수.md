# 가장 큰 수
[프로그래머스 가장 큰 수](https://programmers.co.kr/learn/courses/30/lessons/42746)
* 정렬 : Level2(javascript)

## 풀이
```javascript
function solution(numbers) {
    var answer = '';
    answer = numbers.map(n => n + "").sort((a, b) => (b + a) - (a + b)).join("")
    
    
    return answer[0] == "0" ? "0" : answer;
}
```
```
숫자 + "" = 문자열
```
