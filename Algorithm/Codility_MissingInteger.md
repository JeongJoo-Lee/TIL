# MissingInteger
* 분류 : Counting Elements
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125965077-5f809ae3-093d-44a6-97c3-c1783ea7e024.png)
## 최초 풀이
```javascript
function solution(A) {
    let s = new Set(A.sort((a,b) => a - b));
    let arr = [...s];

    // 모두 음수인 경우와 첫번째 값이 1로 시작하지 않는 경우
    if(arr[0] < 0 || arr[0] !== 1){
        return 1;
    }

    // 빠진 값이 있는 경우
    for (let i = 0; i < arr.length - 1; i++){
        if(arr[i+1] - arr[i] !== 1){
            return arr[i] + 1;
        }
    }

    // 빠진 값이 없는 경우
    return arr[arr.length-1] + 1;
}
```
## 최초 풀이
![image](https://user-images.githubusercontent.com/61656046/125965666-090f202e-474f-4854-81ff-1201cef15787.png)

## 최종 풀이
```javascript
function solution(A) {
    A.sort((a, b) => a - b);
    
    let min = 1;
    
    for (let i in A) {
        if (A[i] > 0 && A[i] == min) {
            min++;
        }
    }
    
    return min;
}
```
## 최종 결과
![image](https://user-images.githubusercontent.com/61656046/125965115-423aee78-1950-4977-ac9a-77bb75812e1c.png)


## 느낀점
* 최솟값을 갱신해나가는 방법이 신박했음
