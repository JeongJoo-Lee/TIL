## 자바스크립트 기본문법(parseInt, parseFloat)

### 형 변환 해주는 문법
* parseInt : number 형태로 변환시켜준다.(정수)
* parseFloat : float 형태로 변환시켜준다.(실수)

```javascript
var height = prompt("키를 입력해주세요");
console.log(height, typeof height);

var height_int = parseInt(height);
console.log(height_int, typeof height_int);

var height_float = parseFloat(height);
console.log(height_float, typeof height_float);
```
```
prompt 로 입력받는 값들은 모두 string 으로 들어오게 되며, 이 값을 형변환 시켜주는 프로그래밍
```
![image](https://user-images.githubusercontent.com/61656046/116837888-29be0680-ac07-11eb-89e1-6f975afb0bc3.png)

<br>

![image](https://user-images.githubusercontent.com/61656046/116837873-1dd24480-ac07-11eb-9d62-ba4f3dd2d05a.png)


