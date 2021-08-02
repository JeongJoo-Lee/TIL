# ☑️ ol, ul, dl 개념 정리
## 🔴 ol (Ordered List)
ol 요소는 Ordered List의 줄임말로, 순서가 있는 목록이다.   
ol 요소 안에 li(list 줄임말)요소로 목록 항목을 표현한다.
### ⚪ 코드예시
```javascript
<ol>
  <li>항목</li>
  <li>항목</li>
</ol>
```   
![image](https://user-images.githubusercontent.com/61656046/127874691-d3e291e8-736e-4b4a-9afc-815aed12d8aa.png)   
* 브라우저의 기본 표현이 숫자이며 css로 로마자 같은 다른 형식으로도 표현 가능하다.

### ⚪ 특징
* ol 요소 안에는 오직 li 요소만 들어올 수 있다. li 안에 다른 것을 넣는건 상관없으며 심지어 li안에 ol요소가 중첩되는것도 가능하다.
* start 속성
```javascript
<ol start="40">
  <li>항목</li>       // 40. 항목 
  <li>항목</li>       // 41. 항목 
</ol>
```
* reversed 속성
```javascript
<ol reversed="reversed">
  <li>항목</li>          // 3. 항목 
  <li>항목</li>          // 2. 항목 
  <li>항목</li>          // 1. 항목 
</ol>
```
## 🔴 ul (Unordered List)
* 순서가 없는 목록 요소이다.
* 자식으로 li 요소만 사용 가능하다.
* ol에서 썼던 start와 reversed는 사용이 불가하다.
### ⚪ 코드예시
```javascript
<ul>
  <li>항목</li>
  <li>항목</li>
  <li>항목</li>
</ul>
```   
![image](https://user-images.githubusercontent.com/61656046/127875541-9a27be6a-015a-4c83-a0de-015c7935423f.png)   

## 🔴 dl (Description List)
* 개념과 정의로 이루어진 형태의 목록이다.
* 개념은 dt요소, 정의는 dd요소로 작성하며 자식요소로 해당 두개의 요소만 사용 가능하다.(dt, dd)
* dt는 인라인 요소, dd는 블럭 요소이다. 때문에 dt안에 블럭요소를 넣으면 안된다.
* dt와 dd는 1:1 형태가 아닌, 1:다수, 다수:1, 다수:다수의 형태를 취할 수 있다.
### ⚪ 코드예시
```javascript
<dl>
  <dt>이름</dt>
  <dt>Name</dt>
  <dd>홍길동</dd>
  <dt>취미</dt>
  <dt>Hobby</dt>
  <dd>축구</dd>
  <dd>Football</dd>
</dl>
```   
![image](https://user-images.githubusercontent.com/61656046/127876531-bc519602-312a-402d-b03c-25853d11b30c.png)




## 💬 정리
* ol 요소는 순서가 있는 목록.
* ul 요소는 순서가 없는 목록.
* ol, ul 요소는 자식으로 li 요소만 올 수 있음.
* li 요소는 블럭 요소로 자신을 포함한 대부분의 블럭 요소를 가질 수 있음
* dl 요소는 개념-정의를 나타내는 목록.
* dl 요소는 자식으로 dt, dd 요소만 올 수 있음.
* dt 요소는 개념을 나타내며 인라인 요소.
* dd 요소는 정의를 나타내며 블럭 요소.
* dt와 dd는 1:1 뿐 아니라 다:다의 형식도 가질 수 있음.
### 코드 요약
```javascript
<h1>라면 레시피</h1>
<dl>
  <dt>준비물</dt>
  <dd>
    <ul>
      <li>물 550cc</li>
      <li>라면봉지</li>
    </ul>
  </dd>
  
  <dt>조리법</dt>
  <dd>
    <ol>
      <li>물을 끓인다.</li>
      <li>물이 끓으면, 면과 스프를 넣는다.</li>
      <li>다 익으면 불을 끄고 맛있게 먹는다.</li>
    </ol>
  </dd>
</dl>
```
### 결과물
![image](https://user-images.githubusercontent.com/61656046/127874377-3fe77980-a6d8-4f9c-b12c-e323774360f3.png)
