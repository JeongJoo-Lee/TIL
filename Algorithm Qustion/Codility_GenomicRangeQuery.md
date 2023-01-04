# GenomicRangeQuery
* 분류 : Prefix Sums(접두사 합계)
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125968024-c7071631-a7ef-4e12-8954-eae8f71f2ba5.png)

## 최초풀이
```javascript
function solution(S, P, Q) {
    let arr = [];
    let answer = [];
    
    for(let i = 0; i < P.length; i++){
        let startIdx = P[i];
        let endIdx = Q[i]
        if (startIdx === endIdx){
            arr.push(S[startIdx]);
        }else{
            arr.push(S.slice(startIdx, endIdx));
        }
    }
    
    arr.map(element => {
        if (element.includes("A")){
            answer.push(1);
        }else if(element.includes("C")){
            answer.push(2);
        }else if(element.includes("G")){
            answer.push(3);
        }else {
            answer.push(4);
        }
    })
    
    return answer;
}
```
## 최초결과
![image](https://user-images.githubusercontent.com/61656046/125967950-d2cc9f2f-a76f-4bd4-80e9-f737f75d5afb.png)

## 최종풀이
```javascript
function solution(S, P, Q) {
    let arr = [];
    let answer = [];
    
    for(let i = 0; i < P.length; i++){
        let startIdx = P[i];
        let endIdx = Q[i]+1;
        arr.push(S.slice(startIdx, endIdx));
    }
    
    arr.map(element => {
        if (element.includes("A")){
            answer.push(1);
        }else if(element.includes("C")){
            answer.push(2);
        }else if(element.includes("G")){
            answer.push(3);
        }else {
            answer.push(4);
        }
    })
    
    return answer;
}
```
## 최종결과
![image](https://user-images.githubusercontent.com/61656046/125968195-08aa27c9-b239-4a4c-9b65-4e272f81cd2b.png)

## 느낀점
* slice 는 마지막항목을 포함시키지 않기 때문에 포함시키려면 + 1 을 해줘야한다는 것을 간과하고 풀어서 틀렸다.
* slice 속성에 대해 다시한번 복습할 수 있는 계기가 되었다.
* **.includes()** 와 **.contains()** 의 차이에 대해 정리 하게 됨
```javascript
//.includes() : 문자열 안에서 특정 문자를 찾을때 사용 
  ex) "String" 에서 t 찾기 -> T/F 값 return
      "String".includes('t');  //true
      
//.contains() : 배열 안에서 특정 원소를 찾을 때 사용 
  ex) [1, 2, 3, 4] 에서 1 찾기 -> T/F 값 return
      [1, 2, 3, 4].contains(1);  //true
```
