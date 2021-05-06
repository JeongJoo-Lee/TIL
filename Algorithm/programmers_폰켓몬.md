# 폰켓몬
[프로그래머스 폰켓몬](https://programmers.co.kr/learn/courses/30/lessons/1845)
* 기출 : 찾아라 프로그래밍 마에스터 
## 나의 풀이
```javascript
function solution(nums) {
    var answer = 0;
    let set = new Set();

    for (const number of nums){
        set.add(number)
    }

    if (set.size <= nums.length/2){
        answer = set.size;
    }else{
        answer = nums.length/2
    }
    return answer;
}
```

## 배운점
### javascript set() 함수 활용법 
* set.add() / set.size    
