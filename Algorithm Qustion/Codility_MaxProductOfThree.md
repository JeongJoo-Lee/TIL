# MaxProductOfThree
* 분류 : sorting(정렬)

## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125816988-22ca3351-bb90-45ef-9786-76927d4a3a2c.png)

## 최초 풀이
```javascript
function solution(A) {
    A.sort((a,b)=>b-a);

    if(A[2] === 0){
        if(A.length > 4){
            return A[0]*A[A.length-2]*A[A.length-1];
        }else{
            return A[0]*A[1]*A[2];
        }
    }else if(A[1] === 0){
        if(A.length > 3){
            return A[0]*A[A.length-2]*A[A.length-1];
        }else{
            return A[0]*A[1]*A[2];
        }
    }

    return A[0]*A[1]*A[2];
}
```
## 최초 결과
![image](https://user-images.githubusercontent.com/61656046/125817064-20f93c76-2886-4594-8f70-2e5dd836a7bd.png)

## 최종 풀이
```javascript
function solution(A) {
    A.sort((a,b)=>b-a);
    
    //+++
    //+--
    //--+
    
    let a = A[0]*A[1]*A[2];
    let b = A[0]*A[A.length-1]*A[A.length-2]

    return Math.max(a,b)
}
```
## 최종 결과
![image](https://user-images.githubusercontent.com/61656046/125817918-17bcad39-0c41-4ab8-851f-7690e0a37293.png)

## 느낀점
* 0 도 값으로 포함될줄알고 풀었는데 틀렸다고 나왔다.
* 그래서 0이 아예 없다고 생각하고 풀었다.
* 양수와 음수만 존재한다는 가정하에 나올 수 있는 최댓값의 구성
  * 가장큰양수(+) * 두번째양수(+) * 세번째양수(+)
  * 가장큰양수(+) * 가장작은음수(-) * 두번째로작은음수(-)
* 대충 이 두가지로 잡고 풀었더니 맞았다.
