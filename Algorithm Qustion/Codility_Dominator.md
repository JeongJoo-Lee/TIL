# Dominator 
* 분류 : Lesson 8, Leader
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/126071502-52c9e291-73bc-4fee-8b5a-30a5291d9670.png)

## 풀이
```javascript
function solution(A) {
    let obj = {};

    for (let i = 0; i < A.length; i++){
        if(obj[A[i]]){
            obj[A[i]].push(i);
        }else{
            obj[A[i]] = [i];
        }

        if (obj[A[i]].length > A.length/2){
            return obj[A[i]][0];
        }
    }
    
    return -1;
}
```
## 결과
![image](https://user-images.githubusercontent.com/61656046/126071519-76d92778-9ae6-4e01-9e72-09a41653a947.png)

## 느낀점
* 값은 변하지않고 해당 값에 대한 인덱스만 추가되는 상황이면 객체를 사용하는것이 제일 깔끔한것 같다고 생각하게 되었다.
```javascript
//ex.
A[0] = 3, A[1] = 3, A[2] = 11, A[3] = 3, A[4] = 11

let obj = {
3 : [0, 1, 3],
11 : [2, 4]
}
```
