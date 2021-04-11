# 협업 프로젝트 전 Git 세팅(했던 내용 기록)

## 1. 깃파일 관리할 로컬 폴더 생성

## 2. Git bash 실행

## 3. 로컬 저장소 생성 : git init

## 4. git branch -M main
* 최초 생성하면 Master 브랜치가 생성되는데 이름을 Main으로 변경

## 5. git remote add origin [원격 깃주소]
* remote를 add(추가) 할껀데 이름은 origin으로 하겠다.
* 로컬저장소와 원격저장소를 연결

## 6. git pull origin main
* pull 먼저함으로서 기본 값들을 세팅해주는듯하다.
* push를 먼저하면 이상하게 에러나서 깃 작업이 진행이 안되는 현상을 경험하였음.
* 위 명령어 뜻은 origin(원격저장소)에 main(브랜치이름)브랜치로부터 pull

## 6. git add [파일명]

## 7. git commit -m "[메세지]"

## 8. git push origin main
* origin(원격저장소)으로 push
