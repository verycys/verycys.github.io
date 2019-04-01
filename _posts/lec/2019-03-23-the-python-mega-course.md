---
title:  "The Python Mega Course: Build 10 Real World Applications"
date:   2019-04-01
last_modified_at: 2019-04-01
---
이 강의노트는 Udemy에서 [Ardit Sulce - The Python Mega Course: Build 10 Real World Applications][1]를 보고 작성하였습니다.

## Getting Started
> 강의를 어떻게 진행해 나갈지, [Pythonanywhere][2]를 통해 console을 다루는 법 등을 설명합니다.

## Python Basics
> Small Code Examples - basics.py: 다음의 코드를 이해하면 Python Basics를 skip해도 됩니다. Python Basics에 대한 정리는 Docs - Python Syntax에 정리하였습니다.

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
> Practice 01: 코드의 출력값은?

```python
mylist = ["Terribly Tricky"]
for word in mylist:
    for letter in word[-6:]
        print(letter)
```
> Practice 02: `fruits.txt`에 나열된 과일들의 스펠링 수를 출력하는 코드는?

```python
myfile = open("fruits.txt")
fruits = myfile.read()
fruits = fruits.splitlines()
for i in fruits:
    print(len(i))
```
> Practice 03: 섭씨를 화씨로 바꾸는 코드는?

```python
def cel_to_fahr(celsius):
    fahrenheit = celsius * 9/5 + 32
    return fahrenheit

temperatures = [10, -20, 100]

for i in temperatures:
    print(cel_to_fahr(i))
```
> Handling Text file - open function

```python
>>> help(open)
Help on built-in function open in module io:
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)

# employees.txt 생성해서 Mike 쓰기
>>> myfile = open("employees.txt", "w")
>>> myfile.write("Mike")
4
>>> myfile.close()

# employees.txt에 Jack and Joe 추가하기
>>> myfile = open("employees.txt", "a")
>>> myfile.write("\nJack\nJoe")
9
>>> myfile.close()

# employees.txt 읽기
>>> myfile = open("employees.txt", "a")
>>> myfile.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
io.UnsupportedOperation: not readable
>>> myfile = open("employees.txt", "a+") # a를 a+로 바꿔야 읽기가 가능함
>>> myfile.read() # Python은 append를 할 것으로 예상하여 커서가 마지막에 위치해 있음
''
>>> myfile.seek(0) # 커서위치를 처음으로 변경
0
>>> myfile.read()
'Mike\nJack\nJoe'
```
> Practice 04: Text file에 1, 2, 3 쓰기

```python
>>> numbers = [1, 2, 3]
>>> file = open("numbers.txt", "w")
>>> for i in numbers:
...     file.write(str(i) + "\n")
file.close()
```

## Beyond the Basics
> For vs While

```python
# for loop는 리스트 안에 있는 모든 것을 반복할 때까지 실행
for item in [1, 2, 3]:
    print(item)

# while loop는 임의의 조건이 만족될 때까지 실행
x = 0
while x < 3:
    print("Smaller")
    x += 1
```
> %s

```python
>>> name = "John"
>>> surname = "Smith"
>>> message = "Hi %s %s, you are logged in!" % (name, surname)
>>> print(message)
Hi John Smith, you are logged in!
```

## Fixing Programming Errors
기본적인 Error들과 Stackoverflow 활용 등에 대한 강의로 이루어져 있습니다.

## Application 1: Build an Interactive Dictionary

## Data Analysis with Pandas

[1]: https://www.udemy.com/the-python-mega-course/
[2]: https://www.pythonanywhere.com
