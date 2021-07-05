# 기능개발
[프로그래머스 기능개발](https://programmers.co.kr/learn/courses/30/lessons/42586)
* 스택/큐 : level 2 (javascript)

## 풀이 
```javascript
function solution(progresses, speeds) {
    let answer = [0];
    let count = 0;
    let days = [];
    
    
    for (let i = 0; i < progresses.length; i++){
        let day = Math.ceil((100 - progresses[i]) / speeds[i])
        days.push(day);
    }
    
    let initDay = days[0];
    
    for (let i = 0, j = 0; i < days.length; i++){
        if(days[i] <= initDay){
            answer[j] += 1;
        }else{
            initDay = days[i];
            answer[++j] = 1;
        }
    }
    
    return answer;
}
```

## 느낀점
* Math.ceil() 활용법 : 같거나 큰수중 가장 작은 수를 리턴한다. ex) 7.333 => 7
* for문에서 두개의 변수를 선언하고 활용할 수 있다.
  * ex) 
```javascript
  for (let i = 0, j =0; i < array.length; i++){};
```
