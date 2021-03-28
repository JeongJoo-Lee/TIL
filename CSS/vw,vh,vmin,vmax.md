# ⚡ vw , vh, vmin, vmax
```
위 속성 모두 뷰포트(Viewport)를 기준으로 하는 길이(length) 값으로, 

문서 또는 모바일 기기 에서 볼 수 있는 부분의 크기를 기준으로 크기를 설정합니다.
```

## ✔️ VW(Viewport Width)
 * 뷰포트 너비의 1% 길이와 동일합니다.
## ✔️ VH(Viewport Height)
* 뷰포트 높이의 1% 길이와 동일합니다.
## ✔️ VMIN(Viewport Minimum)
* 뷰포트 너비 또는 높이를 기준으로 하는 최소 값입니다.
## ✔️ VMAX(Viewport Maximum)
* 뷰포트 너비 또는 높이를 기준으로 하는 최대 값입니다.

- - -

<br>

**vmin, vmax** 값은 뷰포트의 너비, 높이 길이 중 '작은' 혹은 '큰' 길이를 기준으로 값이 동적으로 설정된다.

예를 들어 1000 × 500 크기의 뷰포트가 있다고 했을 때 1vmin 값은 5px 이고, 1vmax 값은 10px로 계산됨

크기가 1200 × 570 으로 변경되면 1vmin은 5.7px, 1vmax는 12px이 된다.

즉, 화면 크기에 상대적으로 변경되는 단위가 뷰포트 단위이다.



[출처](https://webclub.tistory.com/356)
