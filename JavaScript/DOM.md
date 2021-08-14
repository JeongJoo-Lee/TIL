# 목차
* [☑️ BOM & DOM & Node](#%EF%B8%8F-bom--dom--node)
* [☑️ 브라우저 렌더링 과정](#%EF%B8%8F-브라우저-렌더링-과정)
* [☑️ 리플로우 & 리페인트](#%EF%B8%8F-리플로우--리페인트)



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

# ☑️ 리플로우 & 리페인트
## 🔴 Reflow 란? 
* 생성된 DOM 노드의 레이아웃 변경 시 영향을 받는 모든 노드(부모, 자식)의 수치를 다시 계산하여 **레이아웃 트리(렌더 트리)를 재생성**하는 작업을 말한다.
### Reflow를 발생하게 하는 속성
* width, height, padding, margin, float, position 등 **레이아웃에 영향을 주는** 모든 속성

## 🔴 Repaint 란?
* Reflow 과정이 끝나고 재생성된 레이아웃 트리(렌더 트리)를 다시 레이어에 그리는 작업
### Repaint를 발생하게 하는 속성
* color, border-radius, background, box-shadow 등 **시각적으로 보여지는** 모든 속성

### 🟢 정리하면, 리플로우와 리페인트는 렌더링 과정에서 레이아웃 단계와 페인트 단게를 다시(Re) 거치는 과정이다.

### ❓ 리플로우와 리페인트는 렌더링 속도에 왜 중요한 영향을 미칠까?
* 렌더링 과정은 순차적으로 진행된다.
* 각각의 렌더링 과정들은 반드시 전 단계의 데이터가 필요하다.
* 만약 전 단계에 변화가 일어나면 다음 단계에 모두 영향을 미치게 된다.   

![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/61656046/129061767-2e752e47-297b-4788-851c-8ff944cd4dd7.gif)

### 좌에서 우로 이동하는 애니메이션을 만들었다고 가정하자.
* 해당요소가 60fps로 움직일 때 우리 눈에 자연스러워 보일 것이다. 이때 요소의 레이아웃이 변경되기 때문에 렌더링 엔진은 60장의 프레임에 0.1초 간격으로 리플로우, 리페인트 과정을 수행해야한다.

![image](https://user-images.githubusercontent.com/61656046/129063033-f87bcf9e-834a-43fc-b186-a8857b4fd2a1.png)


* 이 과정중에 0.1초 안으로 리플로우, 리펭니트를 끝내지 못한다면 우리눈에는 버벅이는 애니메이션으로 비추어질 것   
![image](https://user-images.githubusercontent.com/61656046/129063251-841b7d02-0128-48bb-919b-511d23006e91.png)

### 결론
* reflow, repaint 해야할 요소가 많으면 많아질 수록 자연스럽지 못한 애니메이션을 그리게 될 것이고, 브라우저의 전체적인 성능에 영향을 미칠수밖에 없다.

## 🔴 성능저하 해결방법
### 🟡 1. CSS Transform 속성을 사용한다.
* transform을 사용하여 만드는 애니메이션은 cpu대신 gpu를 사용하여 화면 렌더링을 처리한다.
* gpu는 여러개의 코어가 간단한 작업을 동시에 협업하는데 특화되어 있기 때문에 애니메이션을 빠르게 처리할 수 있다.

### 🟡 2. requestAnimationFrame 함수를 사용한다.
* requestAnimationFrame 함수는 자바스크립트를 통해 일어나는 애니메이션 정보를 브라우저에 매 프레임마다 미리 알려준다.
* 자바스크립트 애니메이션이 프레임의 시작 시 실행되도록 보장한다.   
 ![image](https://user-images.githubusercontent.com/61656046/129063814-785d1956-cd71-4f93-87d9-06c34728eb1b.png)   
 
 
## 💬 정리
* Reflow란 생성된 DOM 노드의 레이아웃 변경 시 레이아웃 트리(렌더트리)를 재생성하는 작업을 말한다.
* Repaint란 Reflow 과정이 끝나고 재생성된 레이아웃 트리(렌더트리)를 다시 레이어에 그리는 작업이다.
* Reflow, Repaint 작업이 많아질 수록 렌더링 성능이 저하된다.
* 성능 저하를 막기 위해 CSS transform, JS requestAnimationFrame 함수를 사용한다.

---

# ☑️ 이벤트 흐름
## 🔴 브라우저가 사용자의 입력을 받았을때 어떤 일이 일어날까?
### 🟡 1. 브라우저 화면에서 이벤트가 발생한다.
![image](https://user-images.githubusercontent.com/61656046/129450292-60f2da84-2867-4419-9440-a223b9b4a6bd.png)   
* 이때 브라우저 관점에서의 이벤트란, 마우스 클릭 뿐만 아니라 마우스 휠의 움직임, 마우스 포인터의 이동, 화면을 터치하는 등 모든 종류의 사용자 제스처를 말한다.

### 🟡 2. 이벤트가 발생했을 때 브라우저가 제일 먼저하는 일은 이벤트 대상을 찾는 일이다.
![image](https://user-images.githubusercontent.com/61656046/129450304-36e0f4e2-4d63-43f2-a1d6-e436f2525546.png)   
* 이벤트가 발생한 좌표에 무엇이 있는지 확인하기 위해 렌더링 과정중의 하나인 페인트 기록을 찾아본다.

### 🟡 3. 캡처링 단계
![image](https://user-images.githubusercontent.com/61656046/129450318-21a79afb-bf73-469c-a1b2-70e75664503f.png)
* 페인트 기록을 통해 좌표를 알아낸 브라우저는 해당 좌표에 위치한 요소의 이벤트 리스너를 실행한다. 이 과정을 **캡처링 단계(capturing phases)** 라고 한다. 
![image](https://user-images.githubusercontent.com/61656046/129450343-661e1e99-0e7f-4cac-b0af-2de5c46aaa2d.png)
* 이때 타겟 요소의 가장 최상위 window 객체로부터 캡처링 단계의 이벤트 리스너가 등록이 되어 있는지 확인하고, 등록되어있다면 실행한다.
* 그리고 계속 자식 요소로 전파되며 만나는 캡처링 이벤트 리스너를 실행하고 결국 타겟요소까지 이동한다.

### 🟡 4. 버블링 단계
![image](https://user-images.githubusercontent.com/61656046/129450379-ba55f31b-bb2b-4781-a422-a147337e9321.png)
* 캡처링이 끝나고, 최초에 이벤트가 발생했던 요소에 버블링 이벤트 리스터가 있다면 실행한다. 그리고 다음 직계 부모 요소에 버블링 이벤트 리스너가 있다면 실행시키며 가장 최상위 window 객체까지 계속 전파된다.

## 💬 정리
![image](https://user-images.githubusercontent.com/61656046/129450530-52a39e1a-8711-4ba3-83dc-bb79e84e00ea.png)

