# 자바스크립트 기초문법 : Set()

## Set 객체는 자료형에 관계 없이 원시 값과 객체 참조 모두 유일한 값을 저장할 수 있습니다.(중복값을 허용하지 않는다!)

### 선언(new)
```javascript
let set = new Set();
```

### 값 추가(add)
```javascript
set.add(추가할 값)
```

### 객체 길이(size)
```javascript
set.size
```
> set은 length 말고 size를 쓴다.
 
### 값을 갖고있는지 확인(has) : booline 형태로 값을 출력한다.(T/F)
```javascript
set.add(5)

set.has(5)   // true
set.has(4)   // false
```


### Array 객체와의 관계
```javascript
var myArray = ['value1', 'value2', 'value3'];

// Array를 Set으로 변환하기 위해서는 정규 Set 생성자 사용
var mySet = new Set(myArray);

mySet.has('value1'); // true 반환

// set을 Array로 변환하기 위해 전개 연산자 사용함.
console.log([...mySet]); // myArray와 정확히 같은 배열을 보여줌
```



