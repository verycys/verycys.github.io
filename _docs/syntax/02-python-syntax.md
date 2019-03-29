---
title:  "Python Syntax"
date:   2019-03-29
last_modified_at: 2019-03-29
permalink: /docs/python-syntax/
---
제가 필요하다고 생각하는 Python Syntax를 정리하였습니다. 나열순서는 ABC 순입니다.
## Boolean operations
> And, Or, Not

And는 두 값이 모두 True라야 True입니다. 하나라도 False이면 False가 나옵니다. Or는 두 값 중 하나라도 True이면 True입니다. 두 값이 모두 False라야 False입니다. Not은 논리값을 뒤집습니다. 여기서, and, or, not 논리 연산자가 식 하나에 들어있으면 not, and, or 순으로 판단합니다.
```python
korean = 90
english = 81
mathematics = 86
science = 80
print(korean >= 90 and english > 80 and mathematics > 85 and science >= 80)

실행결과: True
```

## Built-in-Function
파이썬 쉘에 `dir(__builtins__)`을 입력하면 파이썬의 내장함수 리스트를 조회할 수 있습니다.

파이썬 쉘에 `dir(list)`을 입력하면 list에 사용할 수 있는 method 리스트를 조회할 수 있습니다. list 대신에 list인 변수명을 입력해도 동일한 결과가 출력됩니다.

파이썬 쉘에 `help(list.append)`을 입력하면 append method에 대한 설명창이 생깁니다.

파이썬 쉘에 `help(len)`을 입력하면 len함수에 대한 설명창이 생깁니다. 종료를 하려면 Q를 누르면 됩니다.

## Class

## Comparison
> Comparison_operator: `<`, `>`, `==`, `<=`, `>=`, `!=`, `is (not)`, `(not) in`

비교 기준은 첫 번째 값입니다. 따라서 첫 번째 값보다 큰지, 작은지처럼 읽습니다. `==`와 `!=`는 값 자체를 비교하고 `is (not)`은 객체를 비교합니다.

## Dictionary
딕셔너리의 `Key`는 문자열뿐만 아니라 정수, 실수, 불도 사용할 수 있으며 자료형을 섞어서 사용해도 됩니다. 그리고 `Value`에는 리스트, 딕셔너리 등을 포함하여 모든 자료형을 사용할 수 있습니다. 단, 키에는 리스트와 딕셔너리를 사용할 수 없습니다.  
`my_dict = {"Key1":"Value1", Key2:Value2, ......}`

```python
# 딕셔너리 만들기
>>> a = dict(one=1, two=2, three=3)
>>> b = {'one': 1, 'two': 2, 'three': 3}
>>> c = dict(zip(['one', 'two', 'three'], [1, 2, 3]))
>>> d = dict([('two', 2), ('one', 1), ('three', 3)])
>>> e = dict({'three': 3, 'one': 1, 'two': 2})
>>> a == b == c == d == e
True

# 딕셔너리 응용
```python
>>> d = {"one": 1, "two": 2, "three": 3, "four": 4}
>>> d[0]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 0
>>> d["one"]
1
>>> type(d["one"])
<class 'int'>
>>> d
{'one': 1, 'two': 2, 'three': 3, 'four': 4}
>>> list(d)
['one', 'two', 'three', 'four']
>>> list(d.values())
[1, 2, 3, 4]
>>> d["one"] = 42 # 값 변경
>>> d
{'one': 42, 'two': 2, 'three': 3, 'four': 4}
>>> del d["two"] # pair 제거
>>> d
{'one': 1, 'three': 3, 'four': 4}
>>> d["two"] = None # pair 추가
>>> d
{'one': 42, 'three': 3, 'four': 4, 'two': None}
```

## Function
예시로 피보나치 수열을 만드는 함수를 정의해 보겠습니다.
```python
def fib(n): # write Fibonacci series up to n
    """
    Print a Fibonacci series up to n.
    """
    a, b = 0, 1
    while a < n:
       print(a, end=' ')
       a, b = b, a+b
    print()

# Now call the function we just defined:
>>> fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```
`def`는 함수를 정의하는 코드입니다. `fib`는 함수의 이름이며 괄호로 싸인 `n`은 `매개변수(parameter)`라고 부릅니다. 함수의 첫 번째 문장에 선택적으로 `Print a Fibonacci series up to n`과 같이 함수에 대한 설명을 추가할 수 있습니다. 이를 독스트링(docstring)이라 합니다. 그리고 함수의 내용을 작성할 때는 반드시 들여쓰기가 되어야 합니다. `fib(2000)`과 같이 함수를 호출할 때 넣는 `2000`을 `인수(argument)`라고 부릅니다.

***
> Default Argument Values

```python
def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)

# Call ask_ok
ask_ok('정말 끝내길 원하세요?')
ask_ok('파일을 덮어써도 좋습니까?', 2)
ask_ok('파일을 덮어써도 좋습니까?', 2, '자, 예나 아니요로만 답하세요!')
```
***
> Keyword Arguments

```python
def cheeseshop(kind, *args, **kwargs):
    print("-- Do you have any", kind, "?")
    print("-- I'm sorry, we're all out of", kind)
    for arg in args:
        print(arg)
    print("-" * 40)
    for kw in kwargs:
        print(kw, ":", kwargs[kw])

# Call cheeseshop
>>> cheeseshop("Limburger", "It's very runny, sir.",
...            "It's really very, VERY runny, sir.",
...            shopkeeper="Michael Palin",
...            client="John Cleese",
...            sketch="Cheese Shop Sketch")

# Return
-- Do you have any Limburger ?
-- I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------
shopkeeper : Michael Palin
client : John Cleese
sketch : Cheese Shop Sketch
```
***
> Unpacking Argument Lists

```python
>>> def print_nums(*args):
...     for i in args:
...         print(i)
...
>>> y = [1, 2, 3]
>>> print_nums(*y)
1
2
3
```
```python
>>> def iPhone(model, price):
...     print("Model:", model)
...     print("Price:", price)
...
>>> x = {'model':'iPhone4', 'price':100}
>>> iPhone(**x)
Model: iPhone4
Price: 100
```
***
> Return vs Print

```python
# test.py
def returning():
    return 10

def printing():
    print 100

returning()
printing()
```
`test.py`를 실행하면 10은 출력이 되지 않고 100만 출력됩니다. `print`는 결과를 출력하지만 `return`은 값만 반환하는 것이기 때문입니다. 만약 함수의 반환값을 재사용하고 싶다면 `print`가 아닌 `return`을 써야합니다. 그 이유를 확인하기 위해 `test.py`를 다음과 같이 수정해보겠습니다.
```python
# test1.py
def returning():
    return 10

def printing():
    print 100

print(returning() + 20)
printing() + 20
```
`test1.py`를 실행하면 30과 100 그리고 Error문구를 확인할 수 있습니다. `returning` 함수에 20을 더한 것은 실행이 되었지만 `printing` 함수에 20을 더한 것은 실행이 되지 않은 것입니다. `returning` 함수의 type은 int이고 `printing` 함수의 type은 NoneType이기 때문입니다. 그러므로 함수의 반환값을 재사용하고 싶다면 `print`가 아닌 `return`을 써야합니다.

## Input and Output with Variable
변수 이름은 원하는 대로 지으면 되지만 다음과 같은 규칙을 지켜야 합니다.
- 영문 문자와 숫자를 사용할 수 있습니다.
- 대소문자를 구분합니다.
- 문자부터 시작해야 하며 숫자부터 시작하면 안 됩니다.
- _ 로 시작할 수 있습니다.
- 특수문자는 사용할 수 없습니다.
- 파이썬의 키워드(if, for, while, and, or 등)은 사용할 수 없습니다.

수학에서 = 기호는 양변이 같다는 뜻이지만 프로그래밍 언어에서 = 기호는 변수에 값을 할당한다는 의미입니다. 수학의 등호와 같은 역할을 하는 연산자는 == 입니다.

변수도 숫자와 마찬가지로 type(변수)로 자료형을 알 수 있습니다.

빈 변수를 만들고 싶을땐 x = None과 같이 None을 할당해주면 됩니다.

변수 여러 개를 한 번에 만들기
```sh
>>> x, y, z = 10, 20, 30 # 변수와 값의 개수가 맞지 않으면 Error가 발생
>>> x = y = z = 10

# 응용
>>> x, y = 10, 20
>>> x, y = y, x
>>> x
20
>>> y
10
```
<br>
변수 삭제
```sh
>>> x = 10
>>> del x
```
<br>
산술 연산 후 할당 연산자 사용하기
```sh
>>> a = 10
>>> a += 20 # a = a + 20과 동일한 의미입니다.
>>> a
30
```
<br>
입력 값을 정수로 변환하기[^2]
```python
a = int(input('첫 번째 숫자를 입력하세요: '))
b = int(input('두 번째 숫자를 입력하세요: '))
print(a + b)
```
<br>
Map을 사용하여 정수로 변환하기
```python
a, b = map(int, input('숫자 두 개를 입력하세요: ').split())
print(a + b)
```
```python
>>> print(1, 2, 3)
1 2 3
>>> print(1, 2, 3, sep=',') # sep에 콤마를 지정, x, a 등 일반적인 문자도 지정 가능
1,2,3
>>> print(1, 2, 3, sep='') # sep에 빈 문자열을 지정
123
>>> print(1, 2, 3, sep='\n')
1
2
3
>>> print('1\n2\n3') # 제어문자
1
2
3
```
```python
print(1, end='') # end에 빈 문자열을 지정하면 다음번 출력이 바로 뒤에 옴
print(2, end='')
print(3)

실행결과: 123
```

## List
파이썬에서 다른 값들을 덩어리로 묶는데 사용되는 여러 가지 컴파운드(compound) 자료형 중 가장 융통성이 있는 것은 리스트 입니다. 리스트는 서로 다른 자료형의 항목들을 포함할 수 있습니다. 예를들어 리스트는 다음과 같이 표현됩니다.  
`days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]`

또는 다음과 같이 리스트를 생성할 수 있습니다.
```python
# List = list(range(시작, 끝, 증가폭))
>>> a = list(range(-4,10,2))
>>> a
[-4, -2, 0, 2, 4, 6, 8]
```

***
> Lists can be indexed and sliced

|   days   | "Mon" | "Tue" | "Wed" | "Thu" | "Fri" | "Sat" | "Sun" |
|:--------:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| positive |   0   |   1   |   2   |   3   |   4   |   5   |   6   |
| negative |   -7  |   -6  |   -5  |   -4  |   -3  |   -2  |   -1  |

```python
>>> days[0:3]
['Mon', 'Tue', 'Wed']
>>> days[:4]
['Mon', 'Tue', 'Wed', 'Thu']
>>> days[:]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
>>> days[-1]
'Sun'
>>> days[0:-1]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']
>>> days[:-2]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri']
>>> days[-4:-1]
['Thu', 'Fri', 'Sat']
>>> days[-4:]
['Thu', 'Fri', 'Sat', 'Sun']
```
`print("Python is fun"[-3:][-1])` 코드의 출력값은 `n` 입니다. `[-3:]`으로 `fun`이 출력되고 `[-1]`로 인해 `n`이 출력됩니다.

***
> Lists support operations like concatenation

```python
>>> days + [55, 66]
['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun', 55, 66]
```

***
> Lists are a mutable type, it is possible to change or add their content

```python
>>> days[1] = "Tuesday"
>>> days
['Mon', 'Tuesday', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
>>> days.append(55)
>>> days
['Mon', 'Tuesday', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun', 55]
```

## Numbers
실수와 정수를 함께 계산하면 표현 범위가 넓은 실수로 계산되며 곱셈, 나눗셈이 덧셈, 뺄셈보다 먼저 계산됩니다. 값을 정수로 만들고 싶을 때는 int()함수를, 실수로 만들고 싶을때는 float()함수를, 객체의 자료형을 알고 싶을 때는 type()함수를 ()안에는 숫자, 계산식, 문자열 등이 들어갈 수 있습니다.
```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6
```
```python
>>> 17 / 3  # classic division returns a float
5.666666666666667
>>>
>>> 17 // 3  # floor division discards the fractional part
5
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> divmod(17, 3)
(5, 2)
```
```python
>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128
```
```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _ # 마지막 계산식인 price * tax가 _에 저장되어 있음
113.0625
>>> round(_, 2)
113.06
```
```python
>>> Ob110 # 2진수
6
>>> Oo10 # 8진수
8
>>> OxF # 16진수
15
```

## Sequence Type — list, tuple, range, text strings
- Mutable Sequence Types: list
- Immutable Sequence Types: tuple, range, text strings
- 시퀀스객체[시작:끝:증가폭]

`days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]`  
`month = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12)`  
`range(1, 6, 2)`는 `list(range(1, 6, 2))`로 될 수 있고 `tuple(range(1, 10, 2))`로도 될 수 있다.

```python
>>> "gg" in "eggs" # 요소값 확인
True
```
```python
>>> days = ("Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun")
>>> len(days) # 요소 개수
7
```
```python
>>> list(range(1, 6, 2)) * 2 # 요소 곱
[1, 3, 5, 1, 3, 5]
```
```python
>>> days[1:6:2] # 요소 증가폭 사용
['Tue', 'Thu', 'Sat']
>>> days[5:1:-1]
['Sat', 'Fri', 'Thu', 'Wed']
```
```python
# 시퀀스객체 연결하기
>>> a = [1, 2, 3]
>>> b = [3, 4, 5]
>>> a + b
[1, 2, 3, 3, 4, 5]
>>> 'Hello,' + str(10)
'Hello,10'
>>> tuple(range(5)) + ('a', 'b') # range는 연산자로 객체를 연결할 수 없습니다
(0, 1, 2, 3, 4, 'a', 'b')
```

## String
파이썬 쉘에서 ''나 ""로 3번 감싸면 여러 줄로 된 문자열을 사용할 수 있습니다. ''와 "" 중 한 가지로 통일하지 않고 여러 가지 방식을 사용하는 이유는 문자열 안에 ''나 ""를 포함시키기 위함입니다.[^1]
```sh
>>> hello = '''Hello, world!
... 안녕하세요
... Python입니다.'''
>>> print(hello)
Hello, world!
안녕하세요
Python입니다.
```
```python
>>> s = ''''Python' is a "programming language"
... that lets you work quickly
... and
... integrate systems more effectively.'''
>>> print(s)
'Python' is a "programming language"
that lets you work quickly
and
integrate systems more effectively.
```
```python
>>> "The sum of 1 + 2 is {}".format(1+2)
'The sum of 1 + 2 is 3'
>>> "The sum of 1 + 2 is {}".format("Three")
'The sum of 1 + 2 is Three'
```
```python
>>> print('C:\some\name')  # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')  # note the r before the quote
C:\some\name
```
제어문자[^3]

## Tuple
튜플은 리스트와 거의 동일하지만 차이점이 있습니다. 괄호가 `[ ]`에서 `( )`로 바뀌며 item들을 변경할 수 없습니다.
```python
>>> days = ("Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun")
>>> days.append(1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'append'
```

## Reference link
- [Python 3.7.3 documentation][1]
- [남재윤 - 파이썬 코딩도장][2]
- [Ardit Sulce - The Python Mega Course][3]

## Footnote

[1]: https://docs.python.org/3/
[2]: https://dojang.io/course/view.php?id=7
[3]: https://www.udemy.com/the-python-mega-course/

[^1]: 따옴표 앞에 `\`를 붙여도 문자열에 따옴표를 포함시킬 수 있습니다. 이러한 방법을 이스케이프라고 부릅니다.
[^2]: Input의 결과를 변수에 저장한 뒤 type을 사용해보면 결과가 문자열(str) 입니다.
[^3]: `\n`: 다음 줄로 이동하며 개행이라고도 부릅니다.  
      `\t`: 탭 문자, 키보드의 Tap키와 같으며 여러 칸을 띄웁니다.  
      `\\`: `\` 문자 자체를 출력
