# MaxProfit 
* 분류 : Lesson 9, Maximum slice problem
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/126071699-364d562b-addf-4ddd-9120-57c8df20427c.png)

## 최초풀이
```javascript
function solution(A) {
    let arr = [];

    if(A.length === 0 || A.length === 1){
        return 0;
    }


    for(let i = 0; i < A.length; i++){
        for (let j = i+1; j < A.length; j++){
            arr.push(A[j] - A[i])
        }
    }
    
    arr.sort((a,b)=>b-a);

    if(arr[0] <= 0){
        return 0;
    }else{
        return arr[0]
    }
}
```
## 최초결과
![image](https://user-images.githubusercontent.com/61656046/126071689-306b4019-983a-4741-b9ad-1a175005e836.png)
## 최종풀이
```javascript
function solution(A) {
    if(A.length === 0 || A.length === 1) return 0;
    let minPrice = A[0];
    let localMax = 0;
    let globalMax = 0;

    for(let i = 1; i < A.length; i++){
        localMax = A[i] - minPrice;
        minPrice = Math.min(A[i], minPrice);
        globalMax = Math.max(localMax, globalMax);
    }

    if(globalMax < 0) return 0;

    return globalMax;
}
```
## 최종결과
![image](https://user-images.githubusercontent.com/61656046/126071722-eb8f9844-0401-4f57-a8aa-d82eb4a1421e.png)

## 느낀점
* 브루트 포스로 풀었다가 런타임 에러가 떠서 퍼포먼스 부분에서 감점을 받았다.
* 부분 합의 최댓값을 구할때는 브루트 포스 보다는 "카데인 알고리즘"이 더 효과적이고 빠르다는 것에 대해 알게됨.
[카데인 알고리즘](https://sustainable-dev.tistory.com/23)
