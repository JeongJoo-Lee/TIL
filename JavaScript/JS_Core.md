# 타입 [*원시타입, *참조타입, *원시 래퍼 타입]
## 원시타입
* 있는 그대로 저장되는 데이터를 표현한다.
## 원시타입의 종류
* boolean : ture, false
* Number : 1, 2, 3...
* String : "Hello World"
* null
* undefined
* Symbol

## 원시타입의 특징
원시값을 변수에 할당하면 값이 복사되어 들어간다.<br>
즉, 원시값이 할당된 변수들은 모두 자기 자신만의 고유한 값을 가지게 된다.

### 코드예시
```javascript
let one = 1;
let two = 2;

one = two;

one = 3;

// 이때 two의 값은?

console.log(two) // 2
```
## typeof
원시값의 종류를 알 수 있게 해주는 매서드<br>
**null의 타입**에 주의할것
### 코드예시
```javascript
console.log(typeof 1);           // Number
console.log(typeof "hi");        // String
console.log(typeof true);        // boolean
console.log(typeof null);        // object
console.log(typeof undefined);   // undefined
```
### 왜 null의 타입은 object인가?
자바스크립트의 초기 버그이다.

---

## 참조타입
* 자바스크립트의 객체를 나타낸다.
## 참조타입의 종류
* 객체 : {}
* 배열 : []
* 함수 : function
* Date
* 정규표현식 : RegExp


원시타입 빼고 전부 참조 타입으로 봐도 무방하다.

## 참조타입의 특징
참조타입은 변수에 값을 직접 저장하지 않는다.
변수에 저장되는 것은 메모리 안에서 **객체의 위치를 가리키는 "포인터"** 입니다.
무엇이 저장되느냐, 이것이 원시 타입과 참조타입의 가장 큰 차이이다.

### 코드예시
```javascript
let objOne = { one : 1 }
let objTwo = { two : 2 }

objTwo = objOne;

console.log(objTwo);  // [object Object] { one : 1 }
//같아졌다.

objTwo.one = 3;

// objTwo 에있는 one의 값을 변경했을때 objOne의 값은?
console.log(objOne);  //  [object Object] { one : 3 }
// objTwo의 바뀐값도 서로 공유한다.
```
값을 공유하는것이 아닌 값을 가리키는 "포인터"를 공유하게 되었기 때문에 **objTwo = objOne** 부분에서부터 같은 참조값(포인터)을 사용하게 된다.
그래서 하나의 값을 변경하면 다른 하나의 값도 영향을 받게 되는것이다.

---

## 원시 래퍼 타입
* 원시 타입을 객체처럼 편리하게 사용하도록 도와준다.

## 원시 래퍼 타입의 종류
* String
* Number
* Boolean

## 원시 래퍼 타입의 특징
원시 타입을 객체처럼 사용하는 순간, 자바스크립트 내부에서 사용하는 데이터의 인스턴스를 만들게 된다.   
이렇게 만들어진 객체는 코드를 실행 후 바로 다음 줄에서 파괴되는데,   
이러한 과정을 **오토박싱(autoboxing)** 이라고 한다.

### 코드예시
```javascript
let name = "bit";

console.log(name.concat("coin"))  // "bitcoin"

// .concat() 은 앞의 문자열과 매개변수로 들어오는 값을 이어붙여준다.
```
* 위 코드의 자바스크립트 내부적 처리 과정(오토박싱 과정)
  ```javascript
  let name = "bit";
  let temp = new String(name);      // 원시타입을 객체처럼 사용하는 순간 임시적으로 생성되는 인스턴스
  console.log(temp.concat("coin")   // 그리고 console.log 가 인스턴스와 함께 실행됨
  temp = null;                      // 볼일을 마쳤으니 인스턴스는 파괴된다.
  ```
* 오토박싱 추가 코드 예시
  ```javascript
  let name = "bit";
  name.coin = "coin";
  console.log(name.coin);     // undefined
  
  // 풀이과정
  let name = "bit";
  let temp = new String(name);    // 객체처럼 사용하려하니 생성된 인스턴스
  temp.coin = "coin";             // 객체처럼 사용
  temp = null;                    // 사용되었으니 다시 파괴
  
  let temp = new String(name);    // 바로 아래에서 객체처럼 사용하려하니 새로 다시 생성된 인스턴스
  console.log(temp.coin);         // 이전에 파괴된 인스턴스에는 값이 할당 되었지만 이번에 다시 생성된 인스턴스(temp)에는 할당된 값이 없음!
                                  // 그래서 undefined 가 출력 됨
  ```
## 정리
* 원시타입은 문자열, 숫자, 불리언, null, undefined, symbol이 있다.
* 참조 타입은 원시타입을 제외한 나머지 데이터 타입이다.
* 원시 타입과 참조타입의 가장 큰 차이는 원시타입은 값 자체가, 참조타입은 데이터의 주소가 저장된다는 것이다.
* 원시 래퍼 타입은 String, Number, Boolean 이다.
* 원시 래퍼 타입은 원시 타입을 객체처럼 사용할 수 있도록 한다.








