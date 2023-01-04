# 키패드 누르기
[프로그래머스 키패드누르기](https://programmers.co.kr/learn/courses/30/lessons/67256)
* 기출 : 카카오 인턴십 2020

## 나의 풀이
```javascript
function solution(numbers, hand) {
    var answer = '';
    let keypad = {
        1 : [1, 1], 2 : [1, 2], 3 : [1, 3],
        4 : [2, 1], 5 : [2, 2], 6 : [2, 3],
        7 : [3, 1], 8 : [3, 2], 9 : [3, 3],
        "*":[4, 1], 0: [4, 2],"#": [4, 3]
    }
    let currentlocationL = [4,1] // 현재 왼 손가락 위치
    let currentlocationR = [4,3] // 현재 오른 손가락 위치
    
    numbers.forEach((num) => {
        let numberlocation = keypad[num] //주어진 숫자의 위치(좌표)
        let distanceL = getDistance(currentlocationL, numberlocation) //왼손위치로부터 거리
        let distanceR = getDistance(currentlocationR, numberlocation) //오른손위치로부터 거리
        
        // 왼손가락 라인에 있을때
        if (numberlocation[1] === 1){
            currentlocationL = numberlocation;
            answer += "L";
        }// 오른손가락 라인일때
        else if(numberlocation[1] === 3){
            currentlocationR = numberlocation;
            answer += "R";
        }//가운데 있을때(거리, 손으로 결정)
        else{
            if (distanceL === distanceR){//거리 같을때
                if(hand === "right"){// 오른손잡이인 경우
                    answer += "R";
                    currentlocationR = numberlocation;
                }
                else{// 왼손잡이인 경우
                    answer += "L";
                    currentlocationL = numberlocation;
                }
            }else if(distanceL < distanceR){//왼손이랑 거리 가까울때
                currentlocationL = numberlocation;
                answer += "L";
            }else{//오른손이랑 거리 가까울때
                currentlocationR = numberlocation;
                answer += "R";
            }
        } 
        })  
    return answer;
}

// 거리구하는 함수
function getDistance(dis1, dis2){
        let result = Math.abs(dis1[0]-dis2[0]) + Math.abs(dis1[1]- dis2[1])
        return result
    }
```

## 배운점
### 좌표로 접근 하는 방법
* 키패드를 좌표로 입력하여 시작부터 좌표로 접근하니 편했다.

### Math.abs
* 거리를 구할때 절댓값을 이용해서 구해야했는데 Math.abs 쓰니 바로 해결되었음
