---
title:  "The Python Mega Course: Build 10 Real World Applications"
date:   2019-03-29
last_modified_at: 2019-03-29
---
이 강의노트는 Udemy에서 [Ardit Sulce - The Python Mega Course: Build 10 Real World Applications][1]를 보고 작성하였습니다.

## Getting Started
> 강의를 어떻게 진행해 나갈지, [Pythonanywhere][2]를 통해 console을 다루는 법 등을 설명합니다.

## Python Basics
> Variables, Strings, Numbers, Built-in Functions, Lists, Tuples, Dictionaries, User Input, Conditionals, Custom Functions, Custom Functions with Multiple Parameters, Opening Files in Python, Working with File Paths, Processing File Content, For Loops, Writing Text to a File, Appending Text to a File

Small Code Examples - basics.py: 다음의 코드를 이해하면 Python Basics를 skip해도 됩니다. Python Basics에 대한 정리는 Docs - Python Syntax에 정리하였습니다.
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

## Beyond the Basics

[1]: https://www.udemy.com/the-python-mega-course/
[2]: https://www.pythonanywhere.com
