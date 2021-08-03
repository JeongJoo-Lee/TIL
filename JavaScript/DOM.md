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




