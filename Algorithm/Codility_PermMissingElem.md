# PermMissingElem
* 시간복잡도

## 문제 설명
```
N개의 서로 다른 정수로 구성된 배열 A가 제공됩니다. 배열에는 [1..(N + 1)] 범위의 정수가 포함되어 있습니다. 
이는 정확히 하나의 요소가 누락되었음을 의미합니다.

당신의 목표는 누락된 요소를 찾는 것입니다.


배열 A가 주어지면 누락된 요소의 값을 반환합니다.

예를 들어, 주어진 배열 A는 다음과 같습니다.

A[0] = 2 A[1] = 3 A[2] = 1 A[3] = 5

함수는 누락된 요소이므로 4를 반환해야 합니다.

다음 가정에 대한 효율적인 알고리즘을 작성하십시오 .

N은 [ 0 .. 100,000 ] 범위 내의 정수입니다 .

A의 요소는 모두 별개입니다.

배열 A의 각 요소는 [1..(N + 1)] 범위 내의 정수입니다.

```

## 최초 풀이
```javascript
function solution(A) {
    let arr = A.length === 0 ? [] : A.sort((a, b) => a - b)
    let answer = null;

    for (let i = 0; i < arr.length; i++){
        if(arr[i] !== i+1){
            answer = i+1;
            break;
        }
    }

    return answer
}
```

## 결과
* 점수 : 50점

* 분석 : 런타임 에러

- - -

## 최종 풀이
```javascript
function solution(A) {
    let arr = A.length === 0 ? [] : A.sort((a, b) => a - b)

    for (let i = 0; i < arr.length; i++){
        if(arr[i] !== i+1){
            return i+1;
        }
    }
	
    // 위 반복문을 거쳤지만 return하지 않았을 경우 가장 마지막 값이 누락된 상태를 뜻함
    // N + 1 번째 값
    
    return arr.length + 1
}
```
## 결과
* 점수 : 100점

* 분석 : OK

- - -

## 느낀점
가장 마지막 숫자가 누락됐을 경우를 생각하지 못했다.

예를들어 중간에 중복되는 값이 생길경우
```
ex.  [ 1, 2, 3, 4, 5, 5 ]
```
이때 (N + 1) 번째 값은 6이어야 하나 5가 중복되면서 for 문에서 return 되지 못했을 것.

 

그러면 정답은 배열의 가장 마지막 번째 숫자(arr.length + 1)가 return 되어야 한다.
