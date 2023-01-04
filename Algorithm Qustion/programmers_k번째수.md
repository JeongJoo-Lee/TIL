# K번째 수
[프로그래머스 K번째 수](https://programmers.co.kr/learn/courses/30/lessons/42748)
* 정렬 : level1(javascript)

## 나의 풀이

```javascript
function solution(array, commands) {
    var answer = [];
    for (var i = 0; i < commands.length; i++){
        let selectedArray = array.slice(commands[i][0] - 1, commands[i][1]);
        selectedArray.sort();
        console.log(selectedArray)
        answer.push(selectedArray[commands[i][2] - 1])
        console.log("정답" + answer)
    }
    return answer;
}
```
* sort() 인자 함수 없이 사용하여 테스트 불합격

## 정답
```javascript
function solution(array, commands) {
    var answer = [];
    for (var i = 0; i < commands.length; i++){
        let selectedArray = array.slice(commands[i][0] - 1, commands[i][1]);
        selectedArray.sort((a,b)=>a-b);
        console.log(selectedArray)
        answer.push(selectedArray[commands[i][2] - 1])
        console.log("정답" + answer)
    }
    return answer;
}
```
```
인자 함수 없이 사용하면 문자열로 크기 형변환되어 비교하기때문에 '10'과 '2'를 비교했을 시 '10'이 작게나옴
```
