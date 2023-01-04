# 오픈 채팅방
[프로그래머스 오픈 채팅방](https://programmers.co.kr/learn/courses/30/lessons/42888?language=javascript)
* 기출 : 2019 KAKAO BLIND RECRUITMENT

## 나의 풀이
```javascript
function solution(record) {
    let answer = [];

    let newArr = record.map((v) => v.split(" "));

    //2. 그 후 기록의 마지막 닉네임을 아이디와 매칭합니다.
    //2.1 여기서 Enter와 Change 가 length가 3임을 이용하면 더 쉽게 접근할 수 있습니다.
    let nickName = {};
    for (let i = 0; i < newArr.length; i++) {
        if (newArr[i].length === 3) {
            nickName[newArr[i][1]] = newArr[i][2];
        }
    }

    //3. 그후 닉네임을 통해 출력합니다.
    for (let i = 0; i < newArr.length; i++) {
        if (newArr[i][0] === "Enter") {
            answer.push(nickName[newArr[i][1]] + "님이 들어왔습니다.");
        } else if (newArr[i][0] === "Leave") {
            answer.push(nickName[newArr[i][1]] + "님이 나갔습니다.");
        }
    }

    return answer;
};
```
## 배운점
### javascript 딕셔너리 활용법
* [uid : nickname] 형식으로 change 다 바꾸고 최종적으로 출력만 시킴
* key = value 를 활용하는 방법에 대해 알게됨
