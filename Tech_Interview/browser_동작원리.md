# 브라우저 동작 원리
1. HTML 마크업을 처리하고 DOM 트리를 빌드한다. (**"무엇을"** 그릴지 결정한다.)
2. CSS 마크업을 처리하고 CSSOM 트리를 빌드한다. (**"어떻게"** 그릴지 결정한다.)
3. DOM 및 CSSOM 을 결합하여 렌더링 트리를 형성한다. (**"화면에 그려질 것만"** 결정)
4. 렌더링 트리에서 레이아웃을 실행하여 각 노드의 기하학적 형태를 계산한다. (**"Box-Model"** 을 생성한다.)
5. 개별 노드를 화면에 페인트한다.(or 래스터화)

## Reference
* [Naver D2 - 브라우저의 작동 원리](https://d2.naver.com/helloworld/59361)
* [Web fundamentals - Critical-rendering-path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/?hl=ko)
* [브라우저의 Critical path (한글)](https://m.post.naver.com/viewer/postView.nhn?volumeNo=8431285&memberNo=34176766)


## 출처
[한재엽님 깃허브](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/FrontEnd#%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC)
