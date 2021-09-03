# 🥇 Rebase 활용해 커밋 날짜 변경하기


## 1. git add .

## 2. git commit -m "메세지"

```
여기서부터 진짜
```

## 3. git log
* 날짜를 변경할 커밋의 이전 커밋 hash값을 복사한다.   


![image](https://user-images.githubusercontent.com/61656046/132023913-8cb34aa1-e859-4443-998f-62ac4b37e778.png)

## 4. git rebase [hash 값] -i
![image](https://user-images.githubusercontent.com/61656046/132024494-09e9635d-e25a-413d-aea0-afd96daec88e.png)   
그러면 해당 커밋 이후의 모든 커밋들이 편집창에 나오게 된다.

### 4-1. a 입력으로 편집모드 전환
![image](https://user-images.githubusercontent.com/61656046/132024950-e361876c-19ed-4a6d-9856-83995dbbfa36.png)
* a 를 입력하면 가장 밑에 **-- INSERT --** 가 생기는데 이때 편집이 가능하다.

### 4-2. edit 로 내용 변경 후 esc 버튼
![image](https://user-images.githubusercontent.com/61656046/132025173-3ed6e175-218d-47b8-b55f-b3762cfe135b.png)   
수정할 커밋의 선택내용을 edit 로 수정해준다. 그리고 esc 버튼으로 수정을 마친다.

### 4-3. :wq! 입력으로 변경내용 적용

![image](https://user-images.githubusercontent.com/61656046/132025476-d8c6d376-8709-465c-8030-8b5c5274daab.png)   
* 그러면 브랜치명 옆에 REBASE라고 입력된 것을 볼 수 있다.

## 5. 변경할 날짜 명령어 입력
```
GIT_COMMITTER_DATE="{변경할날짜}" git commit --amend --no-edit --date "{변경할날짜}"

// 예시 (21.08.16, 10:00:00)
GIT_COMMITTER_DATE="Aug 16 10:00:00 2021 +0900" git commit --amend --no-edit --date "Aug 16 10:00:00 2021 +0900"
```   
![image](https://user-images.githubusercontent.com/61656046/132026661-4f92325b-2ccf-49da-a88d-766b0eb03538.png)   
## 6. git rebase --continue 입력으로 변경사항 적용
![image](https://user-images.githubusercontent.com/61656046/132026760-b918fe56-4f5b-4e5c-acc4-fba2ec65a767.png)   
* 적용이 끝나면 브랜치 옆에 있던 REBASE 문자가 사라진다.

## 7. git log 를 통해 확인 및 push
![image](https://user-images.githubusercontent.com/61656046/132027428-ffbd4258-d6a4-4d34-994c-5c377ea712b5.png)   
* git log 에서 날짜가 변경 된 것을 확인 할 수 있다. 끝.









