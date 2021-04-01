# ⚓ 버블링
```
버블링(bubbling)의 원리는 간단합니다.

한 요소에 이벤트가 발생하면, 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러가 동작합니다. 

가장 최상단의 조상 요소를 만날 때까지 이 과정이 반복되면서 요소 각각에 할당된 핸들러가 동작합니다.

3개의 요소가 FORM > DIV > P 형태로 중첩된 구조를 살펴봅시다. 요소 각각에 핸들러가 할당되어 있습니다.

```
* 예제코드
```JavaScript
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```
![image](https://user-images.githubusercontent.com/61656046/113309340-02db8e80-9342-11eb-94d9-2e273519e0cd.png)
- - -


### ✔️가장 안에있는 P 클릭시 발생하는 상황
![image](https://user-images.githubusercontent.com/61656046/113309388-0f5fe700-9342-11eb-841d-99ebf9b58187.png)
<br>

![image](https://user-images.githubusercontent.com/61656046/113309429-1981e580-9342-11eb-8df4-33b7355ac0e5.png)
<br>

![image](https://user-images.githubusercontent.com/61656046/113309459-20a8f380-9342-11eb-805e-1db435cc6b31.png)
- - -


1. p 에 할당된 onclick 핸들러가 동작합니다.
2. 바깥의 div 에 할당된 핸들러가 동작합니다.
3. 그 바깥의 form 에 할당된 핸들러가 동작합니다.
4. document 객체를 만날 때까지, 각 요소에 할당된 onclick 핸들러가 동작합니다.
- - -


* 이미지 예시

![image](https://user-images.githubusercontent.com/61656046/113309775-72ea1480-9342-11eb-8193-505c306e1fe8.png)

### ✔️이런 흐름을 '이벤트 버블링’이라고 부른다. 
```
이벤트가 제일 깊은 곳에 있는 요소에서 시작해 부모 요소를 거슬러 올라가며 발생하는 모양이 마치 물속 거품(bubble)과 닮았기 때문입니다.
```


[출처](https://ko.javascript.info/bubbling-and-capturing)




