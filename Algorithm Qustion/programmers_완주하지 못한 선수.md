# 완주하지 못한 선수

[프로그래머스 완주하지 못한 선수](https://programmers.co.kr/learn/courses/30/lessons/42576)
* 해시 : level 1

## 풀이
```javascript
function solution(participant, completion) {
    var answer = "";
    
    participant.sort();
    completion.sort();
    
    for (let i = 0; participant.length; i++){
        if (participant[i] !== completion[i]){
            return answer = participant[i];
        }
    }
    return answer;
}
```
