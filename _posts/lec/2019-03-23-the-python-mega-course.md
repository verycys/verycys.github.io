---
title:  "The Python Mega Course: Build 10 Real World Applications"
date:   2019-03-23
last_modified_at: 2019-03-23
---
이 강의노트는 Udemy에서 [Ardit Sulce - The Python Mega Course: Build 10 Real World Applications][1]를 보고 작성하였습니다.

## Getting Started
강의를 어떻게 진행해 나갈지, [Pythonanywhere][2]를 통해 console을 다루는 법 등을 설명합니다.

## Python Basics
> Variables, Strings, Numbers, Built-in Functions, Lists, Tuples, Dictionaries, User Input, Conditionals, Custom Functions, Custom Functions with Multiple Parameters, Opening Files in Python, Working with File Paths, Processing File Content, For Loops, Writing Text to a File, Appending Text to a File

Small Code Examples - basics.py
```python
address = ["Flat Floor Street", "18", "New York"]
pins = {"Mike":1234, "Joe":1111, "Jack":2222}
print(address[0], address[1])
pin = int(input("Enter your pin: "))
def find_in_file(f):    
    myfile = open("sample.txt")
    fruits = myfile.read()
    fruits = fruits.splitlines()
    if f in fruits:
        return "That fruit is in the list."
    else:
        return "No such fruit found!"

if pin in pins.values():
    fruit = input("Enter fruit: ")
    print(find_in_file(fruit))
else:
    print("Incorrect pin!")
    print("This info can be accessed only by: ")
    for key in pins.keys():
        print(key)
```

파이썬 프로그램은 data objects, functions, variables로 이루어져 있습니다. 이 구성요소들의 상호작용으로 파이썬 프로그램은 작동합니다.

파이썬 쉘에 `dir(__builtins__)`을 입력하면 파이썬의 내장함수 리스트를 조회할 수 있습니다.

파이썬 쉘에 `round(10.6)`을 입력하면 11이 출력됩니다.

파이썬 쉘에 `help(len)`을 입력하면 len함수에 대한 설명창이 생깁니다. 종료를 하려면 Q를 누르면 됩니다.

***
Lists

|   days   | "Mon" | "Tue" | "Wed" | "Thu" | "Fri" | "Sat" | "Sun" |
|:--------:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| positive |   0   |   1   |   2   |   3   |   4   |   5   |   6   |
| negative |   -7  |   -6  |   -5  |   -4  |   -3  |   -2  |   -1  |

```sh
>>> days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
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
<br>
파이썬 쉘에 `dir(list)`을 입력하면 list에 사용할 수 있는 method 리스트를 조회할 수 있습니다. list 대신에 list인 변수명을 입력해도 동일한 결과가 출력됩니다.

파이썬 쉘에 `help(list.append)`을 입력하면 append method에 대한 설명창이 생깁니다.

`print("Python is fun"[-3:][-1])` 코드의 출력값은 `n` 입니다. `[-3:]`으로 `fun`이 출력되고 `[-1]`로 인해 `n`이 출력됩니다.

***
Tuples

[1]: https://www.udemy.com/the-python-mega-course/
[2]: https://www.pythonanywhere.com
