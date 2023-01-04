# Distinct (고유값 갯수 찾기)
* 분류 : sort(정렬)

## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/125813098-e3425142-551f-45a5-87e0-d67cf92c4420.png)

## 풀이
```javascript
function solution(A) {
    let s = new Set(A.sort((a,b)=>a-b))
    let arr = [...s];
    
    return arr.length;
}
```

## 결과
![image](https://user-images.githubusercontent.com/61656046/125813228-60a5faec-deb6-4395-bf0c-5418310dace8.png)

## 느낀점
* 너무쉬워서 예외처리 해야 될 것 없는지 조마조마하게 풀게되는듯 하다. codility 문제 종특
