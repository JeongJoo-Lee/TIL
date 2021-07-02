# H-index
[프로그래머스 H-index](https://programmers.co.kr/learn/courses/30/lessons/42747)
* 정렬 : level 2(javascript)

## 풀이
```javascript
function solution(citations) {
    var answer = 0;
    
    citations.sort((a,b) => (b - a))
    // h의 최댓값은 citations의 갯수 즉 1부터 쭉쭉 올라가면서 최댓값과 비교해가면 됨
    
    while(answer <= citations.length){
        if(answer + 1 <= citations[answer]){
            answer++
        }else break;
    }
    
    return answer;
}
```
## 배운점
```
sort((a,b) => (b - a))

//내림차순정렬
```
