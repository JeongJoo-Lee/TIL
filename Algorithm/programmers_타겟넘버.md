# 타겟넘버
[프로그래머스 타겟넘버](https://programmers.co.kr/learn/courses/30/lessons/43165)
* DFS & BFS : level 2

## 풀이
```javascript
function solution(numbers, target) {
  let answer = 0;
  getAnswer(0, 0);
  function getAnswer(x, value) {
    if (x < numbers.length) {
      getAnswer(x + 1, value + numbers[x]);
      getAnswer(x + 1, value - numbers[x]);
    } else {
      if (value === target) {
        answer++;
      }
    }
  }
  return answer;
}
```

## 느낀점
* 이해가 되지 않아서 다른사람의 풀이를 통해 이해하려고 노력한 문제
* 아직도 완벽히 이해되지않았다. DFS&BFS 풀이 접근법 논리와 이 문제 논리를 제대로 파악하고 다시 복기하면서 풀어봐야할듯 하다.
* Javascript를 통해 DFS&BFS 구현이 아직은 많이 서툴다. 기출 문제를 많이 접해야겠다. 
