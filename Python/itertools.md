# :sparkles:파이썬 내장함수 itertools
* 사용법
```python
from itertools import OOO()
```
<br>

- - -

<br>

## permutations(iterable, r=None) (순열)

```python
permutations('ABCD', 2)

**결과**

AB AC AD BA BC BD CA CB CD DA DB DC
```
* r이 지정되지 않았거나 None이면, r의 기본값은 iterable의 길이이며 가능한 모든 최대 길이 순열이 생성된다.  
<br><br>

## combinations(iterable, r=None) (조합)
```python
combinations('ABCD', 2)

**결과**

AB AC AD BC BD CD
```
* 입력 iterable의 순서에 따라 사전식 순서로 방출된다.('ABCD') 따라서, 입력 iterable이 정렬되어있으면, 조합 튜플이 정렬된 순서로 생성된다.    
<br><br>
## combinations_with_replacement(iterable, r=None) 
```python
combinations_with_replacement('ABCD', 2)

**결과**

AA AB AC AD BB BC BD CC CD DD
```
* 개별 요소를 두번이상 반복 할 수 있음(ex. AA)

- - -
[자료출처](https://python.flowdas.com/library/itertools.html#itertools.product)
