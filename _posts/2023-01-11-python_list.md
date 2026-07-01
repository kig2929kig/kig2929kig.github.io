
# 파이썬 - 리스트(list)  

* 리스트(list)는 다양한 값(숫자, 문자 등)을 묶어서 표현할 수 있는 자료형.  
* 대괄호 사이에 쉼표(,)로 구분된 값(항목)들의 목록으로 표현함.
* 서로 다른 자료형의 항목들을 포함할 수 있지만, 항목들이 모두 같은 자료형인 경우가 많음.

## 리스트 초기화


```python
empty_lst = []              
string_lst = ['a', 'b', 'c'] 
integer_lst = [1, 2, 3, 4]    
lst_of_lists = [[1,2,3], ['a', 'b', 'c']] 
lst_of_tuples = [(1, 'a'), (2, 'b'), (3, 'c')]
print(empty_lst)
print(string_lst)
print(integer_lst)
print(lst_of_lists)
print(lst_of_tuples)
```

    []
    ['a', 'b', 'c']
    [1, 2, 3, 4]
    [[1, 2, 3], ['a', 'b', 'c']]
    [(1, 'a'), (2, 'b'), (3, 'c')]


## 인덱싱과 슬라이싱


```python
lst = [1, 'a', 2, 'b', 3, '가']
print(lst[0])
print(lst[-1])
print(lst[-3:])
print(lst[:])
```

    1
    가
    ['b', 3, '가']
    [1, 'a', 2, 'b', 3, '가']


## 리스트 연결(Concatenating lists)


```python
lst = [1, 2, 3] + [4, 5, 6]
print(lst)
lst = lst + ['a', 'b', 'c']
print(lst)
```

    [1, 2, 3, 4, 5, 6]
    [1, 2, 3, 4, 5, 6, 'a', 'b', 'c']


## 리스트의 값을 변경


```python
lst = [1, 2, 4, 5, 9]
lst[3] = 10
print(lst)
```

    [1, 2, 4, 10, 9]


## 리스트의 값을 삽입, 삭제


```python
lst = [1, 2, 3, 4, 10, 9]
lst.insert(4, 5)
print(lst)
del lst[4]
print(lst)
```

    [1, 2, 3, 4, 5, 10, 9]
    [1, 2, 3, 4, 10, 9]


## 슬라이싱을 이용한 리스트의 값 변경


```python
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
print(letters)
letters[2:5] = ['C', 'D', 'E']
print(letters)
letters[2:5] = []
print(letters)
letters[:] = []
print(letters)
```

    ['a', 'b', 'c', 'd', 'e', 'f', 'g']
    ['a', 'b', 'C', 'D', 'E', 'f', 'g']
    ['a', 'b', 'f', 'g']
    []


## append() - 리스트의 끝에 항목을 추가가


```python
lst = [1, 2, 3, 4, 10, 9]
lst.append(4**3)
lst.append("공정")
lst.append((5, '정의'))
print(lst)
```

    [1, 2, 3, 4, 10, 9, 64, '공정', (5, '정의')]


## index() - 리스트 값의 인덱스 번호를 출력


```python
lst = [1, 2, 3, 4, 10, 9]
print(lst.index(10))

```

    4


## len() - 리스트 항목의 수를 계산


```python
letters = ['a', 'b', 'c']
print(len(letters))
```

    3


## 정렬과 반전(reversing)


```python
lst = [4, 5, 1, 9, 2]
lst.sort()
print(lst)
lst.reverse() #리스트의 항목을 끝에서부터 출력
print(lst)
```

    [1, 2, 4, 5, 9]
    [9, 5, 4, 2, 1]


# 리스트 항목을 이용한 반복


```python
lst = ['first', 'second', 'third']
for str in lst:
  print('this entry is %s' % str)

set = [('사과', 'apple'), ('바나나', 'banana') ]
for korean, english in set:
  print('한국어 %s는 영어로 %s입니다.' % (korean, english))
```

    this entry is first
    this entry is second
    this entry is third
    한국어 사과는 영어로 apple입니다.
    한국어 바나나는 영어로 banana입니다.


## 리스트의 항목에 포함되어 있는지 확인


```python
if "사과" in ['바나나', '사과', '망고', '포도', '수박']:
  print(True)
if '*' in "abc*123":
  print(True)
```

    True
    True

