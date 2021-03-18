#  파이썬 zip() 함수 사용법

## ☑️ Python에서 zip()이란,
```
1. 내장함수로 같은 길이의 리스트를 같은 인덱스끼리 잘라서 리스트로 반환을 해주는 역할을 한다.

2. 여러 개의 iterable자료형이 개수가 동일할 때 사용한다. 

3. iterable 자료형의 각각의 요소를 나눈 후 순서대로 묶어서 요소 개수만큼 새로운 iterable 자료형을 생성한다. 
   (여기에서 말하는 interable자료형은 리스트, 튜플 같이 반복 가능한 자료형을 의미한다. )
```
<br><br>

![image](https://user-images.githubusercontent.com/61656046/111640385-80ca7080-883f-11eb-9e82-3f8f944cf56a.png)
```
보통 김밥을 말때, 여러가지 재료를 묶고 김밥을 자른다. 

이것과 개념이 비슷하다. 여러가지 List를 김밥말듯이 말아버리고 슬라이스 자르듯 잘라줘서 새롭게 구성해준다.
```
<br><br>

- - -

## ☑️ 김밥 개념 확인하기
<br>

* **zip() 사용 전**
```python
english = ['a', 'b'] 
num = [1, 2] 

for e, n in english, name: 
  print(e, n)

>>> ('a', 'b'), (1, 2)
```
> **('a',1),('b',2)** 가 나오진 않는다.

<br><br>

* **zip() 사용 후**
```python
english = ['a', 'b'] 
num = [1, 2] 

for e, n in zip(english, name): 
  print(e, n)
  
>>> ('a',1),('b',2)
```
> 김밥 자르듯 각 요소의 자리수 끼리 새롭게 합쳐진 것을 알 수 있다.
<br><br>

- - -

## ☑️ 그 외 여러 활용 예시
```python
# 3개의 길이가 같은 리스트
num = [1, 2, 3]
fruit = ['apple', 'banana', 'orange']
color = ['red', 'yellow', 'orange']



# zip 함수로 묶기
zip_list = zip(num, fruit, color)



# 출력값
print(zip_list)

>>> <zip object at 0x000001AC4902B100>
>>> 그냥 출력하면 이렇게 zip type 으로 출력이 되어 내용 확인이 힘들어짐



# list로 변환 후 출력
print(list(zip_list))

>>> [(1, 'apple', 'red'), (2, 'banana', 'yellow'), (3, 'orange', 'orange')]
```
<br>

### for문에서 zip함수를 사용한 예시
```python
for x, y in zip(range(10), range(10)):  # 두개의 0~9까지 숫자모음
   print(x, y)

>>>
0 0
1 1
2 2
3 3
4 4
5 5
6 6
7 7
8 8
9 9
```
<br>


### zip함수를 이용한 dict자료형 생성
```python
dict_num = { x: y for x, y in zip(range(10),range(10))}

>>> {0: 0, 1: 1, 2: 2, 3: 3, 4: 4, 5: 5, 6: 6, 7: 7, 8: 8, 9: 9}
```


<br><br><br>

- - -
[김밥비유 내용발췌](http://pyengine.blogspot.com/2014/03/python-zip.html) / [여러 활용예시 참고 블로그](https://ooyoung.tistory.com/60)



