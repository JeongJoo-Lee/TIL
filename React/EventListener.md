# EventListener 구독 순서
1. ref 잡고 돔에 접근한다.
2. 뭘 해줄건지 정함(mouseover 이면 그거 일어났을때 어떤걸 해주겠다. 라는 함수 만들어주는)
3. componentDidmount 를 통해 등록을 해주었다.
4. 이 컴포넌트가 사라질때에 쓸데없는 Event Listener 가 남아있을 것을 방지 하기위해서 componentWillUnmount에서 구독을 해제해주었음.


![1](https://user-images.githubusercontent.com/61656046/111874097-ef8e0200-89d6-11eb-8d58-70449b3db317.png)
