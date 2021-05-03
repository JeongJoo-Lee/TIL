## 자바스크립트 기본문법(parseInt, parseFloat)

### 형 변환 해주는 문법
* parseInt : number 형태로 변환시켜준다.
* parseFloat : float 형태로 변환시켜준다.

```javascript
var height = prompt("키를 입력해주세요");
console.log(height, typeof height);

var height_int = parseInt(height);
console.log(height_int, typeof height_int);

var height_float = parseFloat(height);
console.log(height_float, typeof heifht_float);
```
```
prompt 로 입력받는 값들은 모두 string 으로 들어오게 되며, 이 값을 형변환 시켜주는 프로그래밍
```
![image](https://user-images.githubusercontent.com/61656046/116837710-87058800-ac06-11eb-8f51-a3a500177819.png)

![image](https://user-images.githubusercontent.com/61656046/116837717-8a990f00-ac06-11eb-810e-abe2c0eab027.png)

