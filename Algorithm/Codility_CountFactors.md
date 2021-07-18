# CountFactors
* 분류 : Lesson 10, Prime and composite numbers
## 문제 설명
![image](https://user-images.githubusercontent.com/61656046/126071836-526a0a83-d3c1-429a-8fd7-35c7a68fc519.png)

## 최초풀이
```javascript
function solution(N) {
    // 소수 여부 우선 판별
    if(N === 1) return 1;
    if(isPrime(N)) return 2;

    let arr = [];
    for(let i = 0; i < N + 1; i++){
        if(arr.includes(N/i)) break; //이미 존재하면 더이상의 루프는의미없음. 종료

        if(N % i === 0 && !arr.includes(N/i)){
            arr.push(i, N/i)
        }
    }
    return arr.length;

    // 소수가 들어왔을 경우
    function isPrime(num){
        let rootNum = Math.sqrt(num);
        if (num === 1) return false;
        if (num % 2 === 0) return false;
        for (let i = 3; i < rootNum; i++){
            if(rootNum % i === 0) return false;
        }
        return true;
    }
}
```
## 최초결과
![image](https://user-images.githubusercontent.com/61656046/126071817-84b85183-8be1-4803-b337-77ebdcf15365.png)

## 최종풀이
```javascript
function solution(N) {
    if(N === 1) return 1;

    let num = 1;

    for (let i = 2; i < Math.sqrt(N); i++){
        if(N % i === 0){
            num++;
        }
    }
    num *= 2;

    if(Math.sqrt(N)%1 === 0) num++;

    return num;
}
```
## 최종결과
![image](https://user-images.githubusercontent.com/61656046/126071941-674ae974-73d8-49b8-9c19-f05df20e821b.png)

## 느낀점
* 정수인지 판별할때는 %1 === 0 이면 정수이다.
* 제곱근값은 해당 숫자의 약수 목록 중앙에 위치한다.(Math.sqrt(x))
  * 제곱근 까지의 약수의 갯수를 두배로하면 보통은 약수의 총 갯수가 나오는데, 제곱근값이 정수일 경우(x%1 === 0) 해당 제곱근도 약수에 포함시켜야 하므로 +1 을 해준다.
