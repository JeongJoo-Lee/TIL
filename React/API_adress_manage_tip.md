# 프로젝트 시 API 정리 활용 팁

## config.js 파일을 따로 생성 후 내부에 api 정리하여 활용
```javascript
// api 통신을 위한 페이지, 프로젝트 규모가 커지게 되면 유용

const config = {
  api: 'http://3.35.169.245:8080',
};

export { config };
```
```


이렇게하면 모듈 파일 내부에서 api를 번잡하게 다 쓰지 않아도 가독성있게 활용이 가능할것 같다.

```
* 실제 사용 코드


![image](https://user-images.githubusercontent.com/61656046/114266206-04870f80-9a30-11eb-9e39-daa0cedfed16.png)




항해99 노유진님의 ['클론코딩'](https://github.com/noh-yj/dano-clone) 코드 참고하였습니다.
배울게 더 있을것 같아서 당분간 계속 들여다 볼 것 같습니다ㅎㅎ
