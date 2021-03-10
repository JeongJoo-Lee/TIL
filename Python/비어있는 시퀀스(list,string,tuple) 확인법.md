# Sequence(string, list, tuple) 비어있는지 확인법

### 빈 sequence(스트링이나 리스트, 튜플)는 False값을 가진다.
* False 라는 값을 이용하여 비어있는지 여부를 확인한다.

```python
if not A:
  print "List is empty"
```
- - -
```python
권장하는 방법

    if not seq:
    if seq:


권장하지 않는 방법

    if len(seq):
    if not len(seq):
```
- - -




![image](https://user-images.githubusercontent.com/61656046/110644016-045cdf80-81f8-11eb-9ab1-0dd9c42419af.png)
> [출처 : python style guide](https://www.python.org/dev/peps/pep-0008/)
