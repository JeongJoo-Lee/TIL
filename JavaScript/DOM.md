# 목차
* [☑️ BOM & DOM & Node](#%EF%B8%8F-bom--dom--node)
* [☑️ 브라우저 렌더링 과정](#%EF%B8%8F-브라우저-렌더링-과정)



---


# ☑️ BOM & DOM & Node
## 🔴 BOM(Browser Object Model)
* 웹 브라우저의 다양한 기능을 객체처럼 다루는 모델

### 🟡 window 객체
* Global Context(전역 공간)이자 브라우저 창을 나타내는 객체이다.
* 전역 변수나 전역 함수의 경우 window의 프로퍼티처럼 작동하게 된다.
  * 코드 예시
  ```javascript
  var testValue = "haha";
  function testFunc(){
    console.log("hahahaha");
  }
  
  testFunc();         // hahahaha
  window.testFunc();  // hahahaha
  window.testValue    // "haha"
  ```
* 중요 프로퍼티
  * innerWidth, innerHeight, screenX, screenY, scrollBy(), scrollTo()

### 🟡 screen 객체
* 사용자 환경의 디스플레이(모니터) 정보를 가지는 객체이다.
* 중요 프로퍼티
  * availHeight, availWidth, width, height, orientation

### 🟡 location 객체
* 사용자가 보고있는 페이지의 URL을 다루는 객체이다.
* 중요 프로퍼티
  * href, reload, replace
  * 코드 설명 
    ```javascript
    location.href                               // 현재 화면의 주소창을 가져옴
    location.href = "https://www.google.com"    // 해당 값을 가진 주소로 이동함(push)

    location.reload                             // 새로고침

    location.replace("https://www.google.com")  // 현재화면을 매개변수값의 주소로 교체(replace)
    ```

### 🟡 navigator 객체
* 웹브라우저 및 브라우저 환경정보를 가지는 객체이다.
* 중요 프로퍼티
  * userAgent

* 이미지 설명
  * navigator
    ![image](https://user-images.githubusercontent.com/61656046/127989873-b30e5f49-a4fe-43b0-be7c-7dc0f3fcadae.png)
  * navigator.userAgent
    ![image](https://user-images.githubusercontent.com/61656046/127990130-be0cb735-25b0-4c95-b4e7-d44c186966e8.png)   
    브라우저가 구동된 환경을 알려줌(데스크탑, 모바일, 패드 등)


## 🔴 DOM(Document Object Model)
* 자바스크립트 Node 객체의 계층화된 트리
![image](https://user-images.githubusercontent.com/61656046/127990454-ba443de4-fd0c-4fc9-90e9-a42a4731b222.png)
* 빨간 상자들 하나하나가 노드 객체이다.


### 🟡 document 노드
* 웹페이지마다 존재하는 객체이다. 웹페이지 안의 모든 컨텐츠를 다루는 시작점이다.
* 중요 프로퍼티
  * title, url, doctype, documentElement, head, body, getElementById, createElement, querySelector, readyState
* readyState
![image](https://user-images.githubusercontent.com/61656046/127991435-34ac5127-387f-4bd5-b3af-273d0b46bdb3.png)


### 🟡 element 노드
* 웹 페이지 안의 각 html 태그 요소들을 의미한다.
* 중요 프로퍼티
  * querySelector, classList, dataset, id, innerHTML, parentNode, nextSibling, previousSibling

## 💬 정리
* BOM은 브라우저의 기능들을 객체 처럼 다루는 모델이다. window, screen, location, navigator 객체 등이 있다.
* DOM은 자바스크립트 노드 객체의 계층화된 트리이다.
* 노드의 종류에는 document, element, text, comment 등이 있다.

---

# ☑️ 브라우저 렌더링 과정
## 🔴 웹 브라우저의 기본 구조
![image](https://user-images.githubusercontent.com/61656046/129050347-0180ccf4-1b1d-464f-8115-63f12f004363.png)


## 🔴 렌더링 엔진이 하는 일
### 🟡 1. 파싱
HTML을 파싱하여 DOM으로 변환한다.   
![image](https://user-images.githubusercontent.com/61656046/129050840-2ec6c582-49e6-47ec-8fb5-25ee23a83e24.png)   

* 오타 혹은 잘못된 문법을 사용했을 경우 예외처리를 한다.
* <link>, <img> 와 같은 태그를 만나면 리소스를 다운로드 한다.
* **script** 태그를 만나면 DOM 파싱을 중단하고 자바스크립트를 해석한다.
 
```
왜 <script> 태그를 만나면 DOM 파싱을 중단할까??

A. <script> 태그 안에 들어있는 javascript 코드중에 DOM 구조를 변경할 수 있는 코드가 있을 수 있기 때문이다.
```
 
### 코드예시
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS EX</title>
</head>
<body>
 <script>
  document.write("<h2>hi~</h2>");
 </script>
 <h1>hello world</h1>
</body>
</html>
```
* **결과**------------------------------------------------------------------------------------------   
 ![image](https://user-images.githubusercontent.com/61656046/129052702-ca5d3bc6-8a73-4a4d-9264-2dc40aa3d847.png)
 

### 🟡 2. 스타일 계산
CSS를 파싱하여 CSSOM으로 변환한다.   
![image](https://user-images.githubusercontent.com/61656046/129053574-7520608a-fe81-4f21-a932-d6812f5e9b4d.png)   
* CSSOM 정보를 통해 DOM 노드에 대한 스타일을 결정한다.
* 결정된 스타일은 크롬 개발자 도구의 computed 항목에서 확인 가능하다.

### 🟡 3. 레이아웃 
레이아웃 트리(렌더트리)를 생성한다.   
![image](https://user-images.githubusercontent.com/61656046/129054063-b59575f1-6d53-4e76-aab7-260d175fd2e7.png)   
* DOM과 계산된 스타일을 따라가며 요소의 크기나 좌표와 같은 정보를 담은 레이아웃 트리를 생성한다.
* 화면에 표현되는 정보면 트리에 담기게 된다. (display:none X, 가상요소 O)

### 🟡 4. 페인트
레이아웃 트리(렌더트리)가 생성되면 이 트리를 따라 페인트 기록이 생성된다.   
![image](https://user-images.githubusercontent.com/61656046/129054558-ec4358e3-7440-4de5-a74b-c9c5ab83b5e6.png)   
* 페인트 기록에는 요소를 렌더링하는 순서가 저장된다. 
* 그리고 지금까지의 정보를 바탕으로 한 페이지를 여러개의 레이어로 나눈 뒤 
* 그 위에 텍스트, 색, 이미지, 보더, 그림자 등의 모든 시각적인 부분을 그리는 작업이 진행된다.

### 🟡 5. 컴포지팅
각각의 레이어를 스크린에 픽셀로 표현하고(레스터링) 나누었던 레이어들을 합성해 페이지를 그린다.   
이를 **컴포지팅** 이라고 한다.   
![image](https://user-images.githubusercontent.com/61656046/129054970-ee3b38ed-ed7c-497d-92f6-9cd861c36928.png)


## 💬 정리
* 파싱 : HTML을 파싱하여 트리 모델을 만든다.
* 스타일 계산 : DOM + CSSOM = 스타일 확정
* 레이아웃 : 요소의 크기와 좌표 정보가 계산된다.
* 페인트 : 레이어 위에 시각적인 부분을 그린다.
* 컴포지팅 : 각각의 레이어를 픽셀화 하고 다시 합성한다.

---






