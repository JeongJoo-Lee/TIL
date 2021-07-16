# Triangle
* 분류 : sorting
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125969353-3e1f5f71-a627-4491-a287-25a0ac9f3129.png)

## 풀이
```javascript
function solution(A) {
    A.sort((a,b)=>(a-b));
    for(let i = 0; i < A.length -2; i++){
        if( A[i] < A[i+1]+A[i+2] && A[i+1] < A[i]+A[i+2] && A[i+2] < A[i]+A[i+1]){
            return 1;
        }
    }
    return 0;
}
```
## 결과
![image](https://user-images.githubusercontent.com/61656046/125966079-7cea983d-8b08-451c-935f-af1247f69c1a.png)
