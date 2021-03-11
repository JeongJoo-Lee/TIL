 # pass, continue, break 차이
 ## pass
 * pass 는 단순히 실행할 코드가 없다는 것을 의미하며, 비워두면 에러인 곳에(def) 사용함으로서 에러를 막는 용도로도 활용된다.
 ```python
 for i in [1, 2, 3]:
    if i:
        print(f"pass {i}")
        pass                      #네 False고 뭐고 그냥 밑에꺼도 출력하러 넘어가세요~ 아무것도 없으니까요~
    print('출력이 될것인가')
 ```
 ```python
 [실행 결과]
 pass 1
 출력이 될것인가
 pass 2
 출력이 될것인가
 pass 3
 출력이 될것인가
 ```
 
 
 ## continue
 * 다음 순번의 loop(반복)를 돌도록 강제하는 것을 의미한다.(현재 행 이하를 실행하지 않고 반복구문 처음으로 돌아감)
 ```python
 for i in [1, 2, 3]:
    if i:
        print(f"continue {i}")
        continue                 #아니 다음꺼 출력안시켜줘 여기서 돌아가
    print('출력이 될것인가')
 ```
 ```python
 [실행 결과]
 continue1
 continue2
 continue3 
 ```
 > **'출력이 될것인가'** 부분에 도달하기도 전에 다음 반복을 돌았다.
 
 ## break
 * 특정 반복문(while, for)에서 loop를 빠져나올때 이용하며, 한번만 빠져나오게 된다.
 * 이중 포문일때 해당 loop만 탈출하고 다음껀 계속 반복돼서 다시 또 다음 loop를 들어갈 수 있다.
 ```python
 for i in range(3):
    print('레디~')
    for j in range(3):
        print('고!')
        break
 ```
 ```python
 [실행결과]
 레디~
 고!
 레디~
 고!
 레디~
 고!
 ```
 > **'고!'** 까지 출력하고 break문에 의해 1번 탈출하였으나 다음 반복에 걸려서 다시 **'고!'** 를 출력하러 돌아가는것이 반복됨
 
