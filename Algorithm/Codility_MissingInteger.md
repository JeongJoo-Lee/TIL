# MissingInteger
* 분류 : Counting Elements
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125965077-5f809ae3-093d-44a6-97c3-c1783ea7e024.png)

## 풀이
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
## 결과
![image](https://user-images.githubusercontent.com/61656046/125965115-423aee78-1950-4977-ac9a-77bb75812e1c.png)


## 느낀점
* 최솟값을 갱신해나가는 방법이 신박했음
