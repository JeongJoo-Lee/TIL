# MaxCounters
* 분류 : Counting Elements
## 문제 설명
```
처음에는 0으로 설정된 N 개의 카운터가 제공되며 두 가지 작업이 가능합니다.

증가(X) - 카운터 X가 1만큼 증가하고,
최대 카운터 - 모든 카운터는 모든 카운터의 최대값으로 설정됩니다.
M개의 정수로 구성된 비어 있지 않은 배열 A가 제공됩니다. 이 배열은 연속 작업을 나타냅니다.

A[K] = X, 1 ≤ X ≤ N인 경우 연산 K는 증가(X),
A[K] = N + 1이면 작업 K는 최대 카운터입니다.
예를 들어, 주어진 정수 N = 5와 배열 A는 다음과 같습니다.

    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
각 연속 작업 후 카운터 값은 다음과 같습니다.

    (0, 0, 1, 0, 0)
    (0, 0, 1, 1, 0)
    (0, 0, 1, 2, 0)
    (2, 2, 2, 2, 2)
    (3, 2, 2, 2, 2)
    (3, 2, 2, 3, 2)
    (3, 2, 2, 4, 2)
목표는 모든 작업 후에 모든 카운터의 값을 계산하는 것입니다.

함수 작성:

기능 솔루션(N, A);

정수 N과 M 정수로 구성된 비어 있지 않은 배열 A가 주어지면 카운터 값을 나타내는 정수 시퀀스를 반환합니다.

결과 배열은 정수 배열로 반환되어야 합니다.

예를 들면 다음과 같습니다.

    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
함수는 위에서 설명한 대로 [3, 2, 2, 4, 2]를 반환해야 합니다.

다음 가정에 대한 효율적인 알고리즘을 작성하십시오 .

N 및 M은 [ 1 .. 100,000 ] 범위 내의 정수입니다 .
배열 A의 각 요소는 [ 1 .. N + 1 ] 범위 내의 정수 입니다.
```
## 최초풀이
```javascript
function solution(N, A) {
    let answer = Array(N).fill(0);
    let maxNum = 0;

    A.forEach(element => {
        if(element <= N && 1 <= element){
            answer[element-1] += 1;
        }else{
            maxNum = Math.max.apply(null, answer);
            answer.fill(maxNum);
        }
    })

    return answer;
}
```
## 최초결과
![image](https://user-images.githubusercontent.com/61656046/125966399-e2ac5152-88f7-48ea-be40-2f8903873d8b.png)

## 최종풀이
```javascript
function solution(N, A) {
    let answer = Array(N).fill(0);
    let maxNum = 0;
    let compareNum = 0;

    A.forEach(element => {
        const index = element -1
        if(element <= N && 1 <= element){
            answer[index] = Math.max(maxNum + 1, answer[index] + 1)
            compareNum = Math.max(answer[index], compareNum);
        }else{
            maxNum = compareNum;
        }
    })
    
    answer = answer.map((element) => Math.max(element, maxNum));

    return answer;
}
```
## 최종결과
![image](https://user-images.githubusercontent.com/61656046/125966750-ff2902dd-fc47-462f-85c3-050b7ea7c221.png)

## 느낀점
* Array.fill() 과 Math.max.apply(null, Array) 떄문에 런타임 에러가 났다.
* 해결하기위해 반복문과정 하나를 없애고 최댓값 구하는 것을 비교해가며 갱신할 변수하나 추가하는 것으로 대체가 가능했다.(compareNum)
* 앞으로 .fill() 과 Math.max.apply() 사용할때 시간복잡도를 고려하고 사용해야겠다.
