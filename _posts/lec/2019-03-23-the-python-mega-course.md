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
> Practice 04: Text file에 1, 2, 3 쓰기

```python
>>> numbers = [1, 2, 3]
>>> file = open("numbers.txt", "w")
>>> for i in numbers:
...     file.write(str(i) + "\n")
file.close()
```

## Beyond the Basics
> Beyond the Basics 중 일부는 Docs - Python Syntax에 정리하였습니다.

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
> Module, Package, Library

- Module is a file which contains python functions , global variables etc. It is nothing but .py file which has python executable code / statement.
- Package is namespace which contains multiple package/modules. It is a directory which contains a special file __init__.py
- Library is collection of various packages. There is no difference between package and python library conceptually.

```python
# Python library 설치, glob2는 예시 중 하나
pip3 install glob2
python3 -m pip install glob2
```
> Practice 01: 다음의 코드는 섭씨를 화씨로 출력하는 함수입니다. text file을 생성하여 50.0, -4.0, 212.0을 쓰는 코드로 변경하세요. (섭씨가 -273.15보다 작으면 어떤 메시지도 쓰면 안됩니다.)

```python
# 변경전
temperatures = [10, -20, -289, 100]
def c_to_f(c):
    if c < -273.15:
        return "That temperature doesn't make sense!"
    else:
        f = c* 9/5 + 32
        return f
for t in temperatures:
    print(c_to_f(t))
```
```python
# 변경후
temperatures = [10,-20,-289,100]
def writer(temperatures, filepath):
    with open(filepath, 'w') as file:
        for c in temperatures:
            if c > -273.15:
                f = c* 9/5 + 32
                file.write(str(f) + "\n")

writer(temperatures, "temps.txt")
```
> Practice 02: Merging Text Files

```python
import glob2
from datetime import datetime

filenames = glob2.glob("*.txt")
with open(datetime.now().strftime("%Y-%m-%d-%H-%M-%S-%f")+".txt", 'w') as file:
    for filename in filenames:
        with open(filename, "r") as f:
            file.write(f.read() + "\n")
```

## Fixing Programming Errors
기본적인 Error들과 Stackoverflow 활용 등에 대한 강의로 이루어져 있습니다.

## Application 1: Build an Interactive Dictionary
> 같은 디렉토리에 있는 data.json파일을 불러와서 유저가 찾는 단어의 정의를 알려주는 사전입니다. 유저가 찾는 단어가 data에 없더라도 가장 유사한 문자열을 가진 단어가 맞는지 확인질문을 합니다.

```python
import json
from difflib import get_close_matches

data = json.load(open("data.json")) # data파일 로드

def translate(w):
    w = w.lower() # 대문자를 소문자로 변경
    if w in data:
        return data[w]
    elif w.title() in data: # if user entered "texas" this will check for "Texas" as well.
        return data[w.title()]
    elif w.upper() in data: #in case user enters words like USA or NATO , like acronyms(두문자어)
        return data[w.upper()]
    elif len(get_close_matches(w, data.keys())) > 0:
        yn = input("Did you mean %s instead? Enter Y if yes, or N if no: " % get_close_matches(w, data.keys())[0])
        if yn == "Y":
            return data[get_close_matches(w, data.keys())[0]]
        elif yn == "N":
            return "The word doesn't exist. Please double check it."
        else:
            return "We didn't understand your entry."
    else:
        return "The word doesn't exist. Please double check it."

word = input("Enter word: ")
output = translate(word)
if type(output) == list:
    for item in output:
        print(item)
else:
    print(output)
```

## Data Analysis with Pandas

[1]: https://www.udemy.com/the-python-mega-course/
[2]: https://www.pythonanywhere.com
