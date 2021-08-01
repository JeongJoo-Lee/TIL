# CSS 속성 초기화 시키기

[meyer css](https://meyerweb.com/eric/tools/css/reset/) 
구글링 후   
![image](https://user-images.githubusercontent.com/61656046/127769990-ea9044ce-019f-43b0-9a66-99a64a875dc6.png)

해당 코드 부분을 복사하여 css 파일 하나를 만들고 붙여넣는다.

위 코드는 브라우저에 적용된 css 태그들의 기본값을 초기화 해준다.

자세한 내용은 해당 코드를 품은 css 파일 적용 전과 후 사진으로 대체한다.


### reset.css 적용 전
![image](https://user-images.githubusercontent.com/61656046/127769960-28953a2c-1485-4fe6-aa99-31e026d5555b.png)

---


### reset.css 적용 후
![image](https://user-images.githubusercontent.com/61656046/127769968-336577a1-6a63-4936-b025-d08f946bb9ce.png)

## 커스터마이징 
커스터마이징도 쉽게 가능하다.

a 태그를 그냥 쓰면 파란색 색상적용과 밑줄이 생기는 text-decoration이 적용되는 것을 볼 수 있는데   
* 예시   
![image](https://user-images.githubusercontent.com/61656046/127770057-1f30eccf-679c-4ba6-a40f-548f5cae4b51.png)
```javascript
a {
  text-decoration : none;
}
```
이런식으로 a 태그에 대한 css에 text-decoration : none을 적용시키면 모든 a 태그는 일반 문자열 스타일로 초기화되어 생성된다.
