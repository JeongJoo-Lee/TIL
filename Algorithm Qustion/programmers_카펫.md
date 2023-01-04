# 카펫
[프로그래머스 카펫](https://programmers.co.kr/learn/courses/30/lessons/42842)
* 완전탐색(브루트포스) : level 2

## 나의 풀이
```javascript
function solution(brown, yellow) {
    var answer = [];
    var temp = brown + yellow;
    var fin = [];
    
    for (let i = 3; i <= temp; i++){
        if (temp % i === 0) answer.push(i);
    }
    
    for (let j = 0; j < answer.length; j++){
        for (let k = 0; k < answer.length; k++){
            if (answer[j] * answer[k] === temp && (answer[j] - 2) * (answer[k] - 2) === yellow){
                fin.push(answer[j]);
            } else if (answer[j] * answer[k] > temp) break;
        }
    }
    fin.sort((a, b) => (b - a));
    if (!fin[1]) {fin.push(fin[0])};
    return fin;
}
```

## 다른사람 풀이
```javascript
function solution(brown, yellow) {
    var answer = [];
    for (var i = 3; i <= (brown+yellow)/i; i++) {
        var x = Math.floor((brown+yellow)/i);
        if( (x-2)*(i-2)=== yellow) {
            break;
        }
    }

    return [x,i];
}
```
* 가로길이와 세로길이를 곱해서 구하는 방법으로 접근해 이중 반복문 없이 구현한듯하다.
