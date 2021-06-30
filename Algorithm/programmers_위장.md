# 위장
[프로그래머스 : 위장](https://programmers.co.kr/learn/courses/30/lessons/42578)
* 해시 : level 2

## 풀이
```javascript
function solution(clothes) {
    var answer = 1;
    
    let clothList = {};
    
    for (let i = 0; i < clothes.length; i++){
        clothList[clothes[i][1]] = (clothList[clothes[i][1]] ? clothList[clothes[i][1]] + 1 : 1); 
    }
    
    for ( let j in clothList){
        answer *= (clothList[j] + 1)
    } return answer - 1;
}
```

## 해설
```
객체로 풀었다.

풀이를 봐도 이해되지 않던 부분은 해당 카테고리옷을 입지 않았을 때도 고려해야 한다는 것이었다.

{(종류 안의 옷들을 입는 경우의수 : 옷의 개수) + (옷을 안입는 경우의 수 1)} * {...}
```
