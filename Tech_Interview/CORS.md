# :pushpin: CORS(Cross-Origin Resource Sharing)
## :heavy_exclamation_mark: CORS에 대해 설명전에 알고 넘어가야할 개념 (origin, SOP)
### 출처(origin)란?
![image](https://user-images.githubusercontent.com/61656046/126332588-4c231626-617a-47bb-841d-4d838b8dff1b.png)
### 연습문제
#### 다음 중 http://localhost 와 동일 출처인 url을 모두 골라보시오.
```
1. https://localhost               // X : Protocol이 다름(https - http)
2. http://localhost:80             // O : 정답
3. http://127.0.0.1                // X : 원래는 같지만 브라우저에서 string type을 구분하기때문에 다른출처로 인식함
4. http://localhost/api/cors       // O : 정답 - 뒤에 경로는(/api/cors) 포트 이후에 나오는거라 출처와 상관없음
```

- Protocal, Host, Port가 같으면 동일 출처 라고 한다.

## SOP(Same Origin Policy)

```jsx
다른 출처의 리소스를 사용하는 것에 제한하는 보안 방식
```

### :speech_balloon: 왜 SOP를 써야 보안에 도움이 되는가?

- 예시

```jsx
-> 페이스북에 로그인을 해서 토큰을 받고 인증을 받는다. (Origin : www.facebook.com)

-> 해커가 사용자에게 구미가 당기는 버그를 담은 메일을 보낸다.(링크포함)

-> 해당 메일에 링크를 클릭하면 사용자 아이디로 스크립트를 실행시키게 한다.
  ex. 특정 계좌로 송금 or 이상한 게시글 작성

-> 이때 페이스북은 출처를 확인을 한다.
 
-> 해킹 링크를 타고 넘어간 출처는 (ex. www.hacker.ck) ! 따라서 페이스북 출처와 다르기때문에 

	접근 자체를 차단한다!! (Same Origin이 아니기때문!)

## Same Origin Policy
```

### 그렇다면 출처가 다른 리소스가 필요하면 어떻게 해야하나?

## 이때 사용하는것이 바로 CORS 이다.

CORS = Cross-Origin Resource Sharing [ 다른 출처의 자원을 공유! ]

```jsx
교차 출처 리소스 공유(Cross-Origin Resource Sharing, CORS)는 추가 HTTP 헤더를 사용하여,
한 출처에서 실행중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을
부여하도록 [브라우저에 알려주는 체제]입니다.

-MOZILLA-
```

# CORS 접근제어 시나리오

- 단순 요청(Simple Request)
- 프리 플라이트 요청 (Preflight Request)
- 인증정보 포함 요청 (Credentialed Request)

## Preflight

- 사전 확인 작업이라 생각하면 편함( ex. 친구집 놀러가기전에 가도되냐 확인하듯)
