# Z-index
* z-index 속성은 위치 지정 요소와, 그 자손 또는 하위 플렉스 아이템의 Z축 순서를 지정합니다. 더 큰 z-index 값을 가진 요소가 작은 값의 요소 위를 덮습니다.

## 구문
```javascript
/* 키워드 값 */
z-index: auto;

/* <integer> 값 */
z-index: 0;
z-index: 3;
z-index: 289;
z-index: -1;   /* 음수 값으로 우선순위를 낮출 수 있음(맨밑으로 깔아버림) */

/* 전역 값 */
z-index: inherit;
z-index: initial;
z-index: unset;
```

## 값 설명
* **auto**
```
박스가 새로운 쌓임 맥락을 생성하지 않습니다. 현재 쌓임 맥락에서의 위치는 부모 요소와 동일합니다.
즉, 생기는 순서대로 차곡차곡 쌓이게 됨.
```

* **integer**
```
현재 쌓임 맥락에서의 위치로 이 값을 사용합니다. 또한 자신만의 쌓임 맥락을 생성하고, 
해당 맥락에서 자신의 위치를 0으로 설정합니다. 이로 인해 자손의 z-index를 자기 외의 바깥 요소와 비교하지 않습니다.

한마디로 크기별로 높낮이가 결정됨
```

## 예제
* **HTML**
```javascript
<div class="dashed-box">Dashed box
  <span class="gold-box">Gold box</span>
  <span class="green-box">Green box</span>
</div>
```
* **CSS**
```javascript
.dashed-box {
  position: relative;
  z-index: 1;
  border: dashed;
  height: 8em;
  margin-bottom: 1em;
  margin-top: 2em;
}
.gold-box {
  position: absolute;
  z-index: 3; /* put .gold-box above .green-box and .dashed-box */
  background: gold;
  width: 80%;
  left: 60px;
  top: 3em;
}
.green-box {
  position: absolute;
  z-index: 2; /* put .green-box above .dashed-box */
  background: lightgreen;
  width: 20%;
  left: 65%;
  top: -25px;
  height: 7em;
  opacity: 0.9;
}
```
## 결과
![image](https://user-images.githubusercontent.com/61656046/112331397-36903600-8cfc-11eb-8a01-3bf4c7abfc62.png)


```
