# 모의고사
[프로그래머스 모의고사]()
* 브루트포스(완전탐색) : level 1(javascript)

## 풀이
```javascript
function solution(answers) {
    var answer = [];
    let p1 = [1, 2, 3, 4, 5];
    let p2 = [2, 1, 2, 3, 2, 4, 2, 5];
    let p3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];
    
    let s1 = answers.filter((elem, idx) => elem === p1[idx % 5] ).length;
    let s2 = answers.filter((elem, idx) => elem === p2[idx % 8] ).length;
    let s3 = answers.filter((elem, idx) => elem === p3[idx % 10] ).length;
    
    let maxNum = Math.max(s1, s2, s3);
    
    if (maxNum === s1) answer.push(1);
    if (maxNum === s2) answer.push(2);
    if (maxNum === s3) answer.push(3);
    
    return answer;
}
```

## 느낀점
```
filter(element, index, array) 활용법 및 예시 정리할 필요 있을듯하다.

아주 유용한 용법인것 오늘 확인
```
