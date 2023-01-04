# CountDiv
* 분류 : Prefix Sums(접두사 합계)
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125967494-50159ddf-3748-4850-a627-12812560d642.png)

## 최초풀이
```javascript
function solution(A, B, K) {
    let cnt = Math.floor(B/K) - Math.ceil(A/K);
    
    if (A % K === 0) cnt += 1;
    
    return cnt;
}
```
## 최초결과
![image](https://user-images.githubusercontent.com/61656046/125967293-3ea01d56-08ba-4ce0-ab47-0807432f1a5f.png)

## 최종풀이
```javascript
function solution(A, B, K) {
    let cnt = parseInt(B/K) - parseInt(A/K);
    
    // A도 K의 배수일 경우 1 추가
    if (A % K === 0) cnt += 1;
    
    return cnt;
}
```
## 최종결과
![image](https://user-images.githubusercontent.com/61656046/125967537-44bca71f-cb41-41cc-84fe-c4371a908313.png)

## 느낀점
* Math.ceil & Math.floor을 잘못써서 틀렸다.
