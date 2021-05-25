# 인증이 필요한 경로로 설정하기(feat. Route, Redirect)
## Private Route
```
로그인을 해야 접근할 수 있고 주소창으로 로그인없이 접근시 지정된 경로로 돌려보내는 기능을 하는 Private Route 컴포넌트를 만들었다.
```

## Code
* PrivateRoute.js 
```javascript
import React from "react";
import { Redirect, Route } from "react-router-dom";

// 로그인 없이 접근시 인트로화면으로 리다이렉트
function PrivateRoute({ component: Component, ...parentProps }) {
  const status = localStorage.getItem("token");

  // 토큰없으면 false(비로그인)
  const is_login = status === null ? false : true;
  return (
    <>
      <Route
        {...parentProps}
        render={(props) =>
          is_login ? <Component {...props} /> : <Redirect to="/" />
        }
      />
    </>
  );
}

export default PrivateRoute;
```
<br/>

* App.js
```javascript
import PrivateRoute from "./PrivateRoute";

function App(props) {
  return (
    <>
      <ConnectedRouter history={history}>
        <Switch>
          <Route path="/" exact component={Intro} />
          <Route path="/login" exact component={Login} />
          <Route path="/signup" exact component={Signup} />
          <Route path="/findpwd" exact component={FindPassword} />
          <Route path="/main">
            <Wrap>
              <PrivateRoute path="/main" component={Navigator} />
              <PrivateRoute path="/main" exact component={MainCalendar} />
              <PrivateRoute path="/main/analysis" exact component={Analysis} />
              <PrivateRoute path="/main/prac" exact component={UseInfo} />
              <PrivateRoute path="/main/mypage" exact component={MyPage} />
            </Wrap>
          </Route>
        </Switch>
      </ConnectedRouter>
    <>
  );
}

export default App;
```

```
이제 로그인 없이는 Navigator, MainCalendar, Analysis, UseInfo, MyPage 컴포넌트 경로로 접근할수 없다.
```
