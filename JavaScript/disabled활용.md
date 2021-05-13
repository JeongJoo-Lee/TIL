# input 속성 중 disabled 활용하기

```
회원가입시 인증번호 발송하는 부분에서 누르면 누른만큼 인증번호가 발송되어 한번클릭하면 이후는 클릭을 못하게 막아야 하는 일이 생겼다.

그래서 input의 속성중 disabled 를 활용하였다.
```
<br/>

## :x: 클릭 전
![image](https://user-images.githubusercontent.com/61656046/118087182-21807b00-b400-11eb-9f3b-21ab050a6072.png)

<br/>

**인증번호 발송** 버튼을 누르면 sendAuth 라는 함수가 실행이 되는 구조이다.

![image](https://user-images.githubusercontent.com/61656046/118087277-470d8480-b400-11eb-9c14-6b140ab73b9c.png)
```
사전에 id를 지정하고 disabled 속성을 내장시켜둔다.
```
<br/>

- - -

### 코드
```javascript
const sendAuth = (e) => {
  document.getElementById(e.target.id).disabled = true;
  dispatch(userActions.SendAuth(email));
}

```



getElementById 를 이용해 해당 element를 가져오고 disabled 속성값을 true로 변경해주면 한번 클릭했을때 버튼이 비활성화된다.

<br/>

## :o: 클릭 후
![image](https://user-images.githubusercontent.com/61656046/118087702-f0547a80-b400-11eb-99ac-d5509bc2fd32.png)
