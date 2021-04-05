# axios 사용중 then 함수 안팎에서 발생한 무시무시한 오류

## 문제상황
* backend로부터 API를 받아오기 전 Mock-API 를 활용하여 테스트를 진행 중 
* post 에 들어갈 데이터를 받아 list로 묶어서 post_list 화면에 출력시키는 것이 목적이었음
* API 잘 받았고 post 데이터들을 post_list 리스트에 잘 담은 상태
* Dispatch 함수가 정상 작동하지 않음
### Code
![image](https://user-images.githubusercontent.com/61656046/113603222-a39db700-967e-11eb-9dcc-7f65e2e7d21b.png)
### Console 창
![image](https://user-images.githubusercontent.com/61656046/113603203-9c76a900-967e-11eb-9519-9f7909b2f5e8.png)
> dispatch 가 먼저 호출이 되고 빈상태로 온다.
<br>


![image](https://user-images.githubusercontent.com/61656046/113603189-9680c800-967e-11eb-8a81-f0227e151458.png)
> 그리고 나서 먼저 작성된 console.log(post_list) 코드가 나오는데 여기서는 정상적으로 잘 찍힌다.
<br>


```javascript
콘솔에 나오는 순서가 뒤죽박죽이었는데 이때 눈치를 챘어야 했다.

코드를 잘 보면
```
```javascript
dispatch(setPost(post_list)); 
```
```
부분이 then 함수 바깥에 적혀있다. 그래서 then이 동작을 하면 dispatch로 넘어가지 않고 다음 runtime으로 작동한 것이었음
```
<br>


## 해결
### Code
![image](https://user-images.githubusercontent.com/61656046/113603873-7271b680-967f-11eb-8d5b-699f32aaac66.png)
> dispatch(setPost(post_list)) 를 then 안에 삽입하였다. 이로써 then일때 함께 동작함
### Console 창
![image](https://user-images.githubusercontent.com/61656046/113603970-98975680-967f-11eb-95f4-2daa9afef45a.png)
> 순서대로 console이 찍혀나옴
 
```
logger 창에서 "action" 부분 뿐만아니라 "next state" 에서도 list: Array(2)로 잘 찍혀서 나오는 것을 확인 할 수 있다.
```

## 느낀점
```
.then() 함수의 사용법을 아주 확실하게 몸으로 깨닫게 되었으며, 정말 한끗 차이의 오차도 아주 큰 차이를 만들수 있다는 것을

제대로 알게됨
```

