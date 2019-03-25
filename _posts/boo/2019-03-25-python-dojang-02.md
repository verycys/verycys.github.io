---
title:  "파이썬 코딩 도장 Unit8 ~ UnitX"
date:   2019-03-25
last_modified_at: 2019-03-25
---
이 북노트는 [남재윤 - 파이썬 코딩 도장][1]을 보고 작성하였습니다. 해당 사이트에서는 각 Unit별로 개념을 학습한 후 바로 연습문제와 심사문제들을 풀 수 있어 처음 파이썬을 공부하는 사람들에게 적합한 것 같습니다. 광고가 거슬린다면 책을 구매한 후 저자에게 인증을 받으면 광고가 없는 사이트에서 학습할 수 있습니다.

## Unit8 불과 비교, 논리 연산자 알아보기
### 비교 연산자
비교 기준은 첫 번째 값입니다. 따라서 첫 번째 값보다 큰지, 작은지처럼 읽습니다.
```sh
>>> 10 > 20
False
>>> 10 <= 10
True
```
<br>
`같다 ==, 다르다 !=`는 값 자체를 비교하고 `is와 is not`은 객체를 비교합니다.
```sh
>>> 1 == 1.0
True
>>> 1 is 1.0
False
>>> 1 is not 1.0
True
```

### 논리 연산자 And, Or, Not
And는 두 값이 모두 True라야 True입니다. 하나라도 False이면 False가 나옵니다. Or는 두 값 중 하나라도 True이면 True입니다. 두 값이 모두 False라야 False입니다. Not은 논리값을 뒤집습니다. 여기서, and, or, not 논리 연산자가 식 하나에 들어있으면 not, and, or 순으로 판단합니다.

```python
korean = 90
english = 81
mathematics = 86
science = 80
print(korean >= 90 and english > 80 and mathematics > 85 and science >= 80)

실행결과: True
```

## Unit9 문자열 사용하기
### 여러 줄로 된 문자열 사용하기
파이썬 쉘에서 ''나 ""로 3번 감싸면 여러 줄로 된 문자열을 사용할 수 있습니다. ''와 "" 중 한 가지로 통일하지 않고 여러 가지 방식을 사용하는 이유는 문자열 안에 ''나 ""를 포함시키기 위함입니다.[^1]
```sh
>>> hello = '''Hello, world!
... 안녕하세요
... Python입니다.'''
>>> print(hello)
Hello, world!
안녕하세요
Python입니다.
>>>
```
```python
s = ''''Python' is a "programming language"
that lets you work quickly
and
integrate systems more effectively.'''
print(s)

실행결과:
'Python' is a "programming language"
that lets you work quickly
and
integrate systems more effectively.
```

## Unit10 리스트와 튜플 사용하기
튜플은 리스트처럼 요소를 일렬로 저장하지만, 안에 저장된 요소를 변경, 추가, 삭제를 할 수 없습니다. 간단하게 읽기 전용 리스트라고 할 수 있습니다. 리스트를 생성할 때는 []대괄호를 사용하고, 튜플을 생성할 때는 ()괄호를 사용합니다.

List = list(range(시작, 끝, 증가폭))
Tuple = tuple(range(시작, 끝, 증가폭))
```sh
>>> a = list(range(-4,10,2))
>>> a
[-4, -2, 0, 2, 4, 6, 8]

>>> b = tuple(range(10,0,-1))
>>> b
(10, 9, 8, 7, 6, 5, 4, 3, 2, 1)
>>> b[3]
7
```

## Unit11 시퀀스 자료형(리스트, 튜플, range, 문자열) 활용하기
### 특정 값이 있는지 확인하기
```sh
>>> a = [1, 2, 3]
>>> 3 in a
True
>>> 'P' in 'Hello, Python'
True
```
### 시퀀스 객체 연결하기
```sh
>>> a = [1, 2, 3]
>>> b = [3, 4, 5]
>>> a + b
[1, 2, 3, 3, 4, 5]
>>> 'Hello,' + str(10)
'Hello,10'
>>> tuple(range(5)) + ('a', 'b')
(0, 1, 2, 3, 4, 'a', 'b')
```
변수를 만들지 않고 리스트 여러 개를 직접 연결해도 상관없습니다. 그러나 range는 연산자로 객체를 연결할 수 없습니다.

### 시퀀스 인덱스

|      days      | "Mon" | "Tue" | "Wed" | "Thu" | "Fri" | "Sat" | "Sun" |
|:--------------:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| positive index |   0   |   1   |   2   |   3   |   4   |   5   |   6   |
| negative index |   -7  |   -6  |   -5  |   -4  |   -3  |   -2  |   -1  |

```sh
# 시퀀스객체
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

# 반복
>>> days * 2
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', '
Sat', 'Sun']

# 요소개수
>>> len(days)
7

# 요소접근: 시퀀스객체[시작:끝:증가폭]
>>> days[-1]
'Sun'
>>> days[len(days)-1]
'Sun'

# 요소 값 할당
>>> days[0] = 1
>>> days
[1, 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']

# 요소제거
>>> del days[1]

# 요소 슬라이스
>>> days[0:3]
['Mon', 'Tue', 'Wed']
>>> days[:4]
['Mon', 'Tue', 'Wed', 'Thu']
>>> days[:]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
>>> days[3:5]
['Thu', 'Fri']
>>> days[0:-1]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']
>>> days[-4:-1]
['Thu', 'Fri', 'Sat']
>>> days[-4:]
['Thu', 'Fri', 'Sat', 'Sun']
>>> days[1:6:2] # 요소 증가폭 사용
['Tue', 'Thu', 'Sat']
>>> days[5:1:-1]
['Sat', 'Fri', 'Thu', 'Wed']
```
## Unit12 딕셔너리 사용하기
딕셔너리의 키는 문자열뿐만 아니라 정수, 실수, 불도 사용할 수 있으며 자료형을 섞어서 사용해도 됩니다. 그리고 값에는 리스트, 딕셔너리 등을 포함하여 모든 자료형을 사용할 수 있습니다. 단, 키에는 리스트와 딕셔너리를 사용할 수 없습니다.

| phone |     1     |     2     |     3     |     4     |
|:-----:|:---------:|:---------:|:---------:|:---------:|
|  Key  | "iPhone4" | "iPhone5" | "iPhone6" | "iPhoneX" |
| Value |    400    |    500    |    600    |    1000   |

```sh
# 딕셔너리
phone = {'iPhone4':400, 'iPhone5':500, 'iPhone6':600, 'iPhoneX':1000}
>>> phone
{'iPhone4': 400, 'iPhone5': 500, 'iPhone6': 600, 'iPhoneX': 1000}

# 값 할당하기
>>> phone['iPhone4']
400
>>> phone['iPhone4'] = 1400
>>> phone
{'iPhone4': 1400, 'iPhone5': 500, 'iPhone6': 600, 'iPhoneX': 1000}

# 값 확인하기
>>> 'iPhone4' in phone
True

# 딕셔너리 수 확인하기
>>> len(phone)
4

# phone 딕셔너리 만들기
>>> phone = dict(iPhone4=400, iPhone5=500, iPhone6=600, iPhoneX=1000)
>>> phone = dict(zip(['iPhone4', 'iPhone5', 'iPhone6', 'iPhoneX'], [400, 500, 600, 1000]))
>>> phone = dict([('iPhone4', 400), ('iPhone5', 500), ('iPhone6', 600), ('iPhoneX', 1000)])
>>> phone = dict({'iPhone4':400, 'iPhone5':500, 'iPhone6':600, 'iPhoneX':1000})
```


[1]: https://dojang.io/course/view.php?id=7

## 각주
[^1]: 따옴표 앞에 `\`를 붙여도 문자열에 따옴표를 포함시킬 수 있습니다. 이러한 방법을 이스케이프라고 부릅니다.
