# 프린터
[프로그래머스 프린터](https://programmers.co.kr/learn/courses/30/lessons/42587?language=javascript)
* 스택/큐 : level 2 (javascript)

## 풀이
```javascript
function solution(priorities, location) {
    let answer = 0;
    let compareArr = [];
    let finArr = [];
    let print;
    
    // 처음 지정한 출력물이 나중에 몇번째로 이동해있는지 찾기위해 인덱스와 함께 있는 형태로 2차 배열을 만들어줌
    priorities.forEach( (elem, idx) => {
        let temp = [idx, elem];
        compareArr.push(temp)
    })
    
    // 비교할 배열의 첫번째 값을 가지고 그 뒷 값들중 큰게 있냐 없냐로 비교배열에서 뺴서 finArr에 담을지 아니면 가장 뒤로 옮길지 결정함
    while(compareArr[0]){
        print = compareArr.shift();
        if(compareArr.some( e => e[1] > print[1] )){
            compareArr.push(print)
        }else{
            finArr.push(print);
        }
    }
    
    // 인덱스로 시작했기때문에 +1 해준다
    answer = finArr.findIndex(e => e[0] == location) + 1;
    return answer;
}
```

## 느낀점
* Array.prototype.some() 활용법에 대해 알게 됨
  * 하나라도 조건에 해당되는것이 있으면 true, 아예없으면 false 리턴한다.
