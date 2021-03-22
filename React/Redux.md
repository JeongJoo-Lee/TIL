# 🦆 Redux 
[자료출처 : 생활코딩](https://www.youtube.com/watch?v=N9PT9iNTZAE&list=PLuHgQVnccGMB-iGMgONoRPArZfjRuRNVc&index=2)
## ✔️개요
![image](https://user-images.githubusercontent.com/61656046/111977715-67c70580-8b46-11eb-8724-547244a87a24.png)
_ _ _

<br>

## ✔️State와 Render의 관계
![image](https://user-images.githubusercontent.com/61656046/111978674-87aaf900-8b47-11eb-90e7-dc493193ea99.png)

```
1. 리덕스의 핵심은 Store

2. Store는 정보가 저장되는 곳

3. Store 안에는 state라는 실제 정보가 저장된다.
   - state는 절대 직접 접속이 불가하다. 누군가를 통해야한다.(getState)

4. reducer

5. render는 UI를 만들어줄, 개발자가 작성할 코드 부분

6. Store에 접근 하기 전에, 일종의 창구 직원 역할하는 함수(dispatch, subscribe, getState)

7. render는 state 값을 참조해서, UI를 만든다.

8. state가 바뀔 때마다, render가 호출되게할 때, subscribe를 사용한다.
```
<br>

- - -


## ✔️Action과 Reducer

![image](https://user-images.githubusercontent.com/61656046/111980434-a5795d80-8b49-11eb-8f3c-9542615a7f85.png)

```
1. submit을 눌렀을 때, 객체 하나를 전송한다. 이때 이 객체를 action이라고 한다.

2. 이 action은 dispatch에 전달된다.

3. dispatch는 2가지 일을 한다.
   - reducer를 호출해서, state 값을 바꾼다.
     - reducer에 현재의 state 값과, action을 값이 주어진다.
     - reducer의 return 하는 객체는 state의 새로운 값이 된다.
     - reducer는 state를 입력 값으로 가지고, action을 참조해서, 새로운 state 값을 만들어서, return 해주는 
       state를 가공해주는 가공자이다.
   - 이후, subscribe를 이용해서, render를 호출한다.
     - 새로운 state에 맞게 UI가 변한다.
```
<br>

- - -


## ⁉️ Redux를 쓰면 좋은 이유
* **사용 전**
![image](https://user-images.githubusercontent.com/61656046/111981406-fd649400-8b4a-11eb-9b2c-4b56034571c3.png)
* **사용 후**
![image](https://user-images.githubusercontent.com/61656046/111981453-0eada080-8b4b-11eb-859c-2fca1f826c93.png)
<br>

* 중앙집중적인 데이터스토어를 통해서 어플리케이션을 쉽게 개발 할 수 있다.
<br>

* 시간여행을 할 수 있다.(사용내역을 타임라인처럼 나열하고 돌아갈 수도 있음)
<br>

- - -

## ✔️Redux의 적용 : store생성

![image](https://user-images.githubusercontent.com/61656046/111984347-9cd75600-8b4e-11eb-9f87-5f2ffb32fbc5.png)

```javascript
function reducer(state, action){
  if(state === undefined){
      return {color:'yellow'}       >>>초기 값 설정
  }
}
var store = Redux.createStore(reducer);      # reducer를 연동시켜 state값 생성
function red() {
  var state = store.getState();                        # getstate를 통해 state값을 가져오는 기능
  document.querySelector('#red').innerHTML = `
    <div class="container" id="component_red" style="background-color: ${state.color}">     # 가져온 state값에서 color만 추출한것
      <h1>red</h1>
      <input type="button" value="fire" onclick="
      document.querySelector('#component_red').style.backgroundColor = 'red';
       ">
    </div>
  `;
}
```
```
스토어를 만들면 내부적으로 State가 생기고 State의 값을 가져올 때는 getState를 써야 한다.

reducer라는 것을 통해서 State값을 만들어줘야 하는데 그때 위코드 처럼 reducer의 state 값이 undefined 상태라면

초기화를 위해서 최초로 실행되는 reducer에 대한 호출이기 때문에

return 에 설정값을 넣으면 그것이 최초 설정값이 된다.
```
<br>

- - -


## ✔️Reducer와 Action을 이용해서 새로운 State값 만들기
```javascript
function reducer(state, action){
  if(state === undefined){
      return {color:'yellow'}     
  }
  var new_state;                                       #  복제본 미리 생성
  if(action.type === 'CHANGE_COLOR'){                          #  action의 type을 확인하고 state값을 변경해야 함
  new_state = Object.assign({}, {state}, {color:'red'})    #  Object.assign 자바스크립트 함수(복제 및 덮어쓰기)
  }
  return new_state
}
var store = Redux.createStore(reducer); 
function red() {
  var state = store.getState();         
  document.querySelector('#red').innerHTML = `
    <div class="container" id="component_red" style="background-color: ${state.color}">     
      <h1>red</h1>
      <input type="button" value="fire" onclick="
        store.dispatch({type:'CHANGE_COLOR', color:'red'});     # 이 값이 action 역할(dispatch를 통해 전달됨)
      ">
    </div>
  `;
}
```

* dispatch에서 **type** 설정은 필수이다.[스토어 안에 있으니 표현은 store.dispatch()]
* recuder : State의 값을 변경해준다.(action과 이전의 State 값을 이용해서 새로운 State값을 return(복제)하고 그것을 State값으로 새롭게 적용시켜준다.)
  * return 하는값은 원본을 변경시키는 것이 아닌, 새로운 값을 생성하고 이전값들에 변경될 값을 덮어씌워주어 변화를 준다. 그래야지만 redux를 이용한 타임트래블링 등을 이용할 수 있게 된다.
<br>

- - -



## ✔️State의 변화에 따라서 UI반영하기(subscribe활용)

![image](https://user-images.githubusercontent.com/61656046/111993059-8387d700-8b59-11eb-8156-7ebbdcf2433f.png)

```javascript
function reducer(state, action){
  if(state === undefined){
      return {color:'yellow'}     
  }
  var new_state;                                     
  if(action.type === 'CHANGE_COLOR'){                 
  new_state = Object.assign({}, {state}, {color: action.color})   # 전달받은 action의 변경하고싶은 값(color)을 새롭게 복제하는 state에 삽입
  }
  return new_state
}
var store = Redux.createStore(reducer); 
function red() {
  var state = store.getState();         
  document.querySelector('#red').innerHTML = `
    <div class="container" id="component_red" style="background-color: ${state.color}">     
      <h1>red</h1>
      <input type="button" value="fire" onclick="
        store.dispatch({type:'CHANGE_COLOR', color:'red'}); 
      ">
    </div>
  `;
}
store.subscribe(red);
red();


var store = Redux.createStore(reducer); 
function blue() {
  var state = store.getState();         
  document.querySelector('#blue').innerHTML = `
    <div class="container" id="component_blue" style="background-color: ${state.color}">     
      <h1>blue</h1>
      <input type="button" value="fire" onclick="
        store.dispatch({type:'CHANGE_COLOR', color:'blue'}); 
      ">
    </div>
  `;
}
store.subscribe(blue);
blue();


var store = Redux.createStore(reducer); 
function green() {
  var state = store.getState();         
  document.querySelector('#green').innerHTML = `
    <div class="container" id="component_green" style="background-color: ${state.color}">     
      <h1>green</h1>
      <input type="button" value="fire" onclick="
        store.dispatch({type:'CHANGE_COLOR', color:'green'}); 
      ">
    </div>
  `;
}
store.subscribe(green);               #subscribe를 통해 state값이 변할때마다 render에 전달
green();
```
* Redux를 사용하는 이유
  * redux를 사용하지 않을때는 각 컴포넌트끼리의 종속성이 강해서 해당 컴포넌트의 삭제나 업데이트, 새로운 컴포넌트의 추가를 할때 굉장히 번거로운 작업이 필요하지만 redux를 사용하여 store를 이용한 중앙집중식 데이터 관리를 통해 각 컴포넌트의 독립성이 높아져 각 컴포넌트의 추가 삭제 업데이트에 있어 다른 컴포넌트들과 연관이 되지않아 훨씬 효율적이 되었다. 그리고 이러한 state에 접근할때 dispatch로 state변경, subscribe로 state에 맞는 rendering, getState()로 해당 state에 접근을 통해 직접적으로 state에 접근하여 발생하는 오류를 줄일수 있다. redux 과정: 해당 컴포넌트에서 action을 실행시키는 dispatch를 통해 reducer의 기존 state와 해당 action을 통해 내가 사용할 새로운 state값을 리턴한다. 그 state값을 getState로 store에서 꺼내와서 해당 컴포넌트가 사용하는데 state가 바뀌면(변경되면) 해당 컴포넌트가 render되도록 store에 subscribe(구독)을 한다.
  *   리덕스를 사용하지 않을때는 직접 다 props를 부모와 자식간의 관계에 가져와서 연관되어 사용됨으로써 각각 전달된 값을 전달 및 가져와서 사용하였습니다. 이렇게 함으로써 하나의 컴포넌트가 사라지거나 변경될때 각 컴포넌트 수정을 해야하는 부분이 많았는데 리덕스를 사용함으로써 부모와 자식간의 컴포넌트 관계를 끊음으로써 연관 된 값을 각각 전달할 필요가 없어져서 훨씬 하나의 컴포넌트에 더 집중되도록 코딩할수 있습니다. 하나의 store안에 집중되게 사용하여 각각의 전달값을 만들 필요가 없도록 하는것이 리덕스를 사용하는 이유입니다.
