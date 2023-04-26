20 Python Concepts I Wish I Knew Way Earlier
# Stuff I wish I learnt earlier as a beginner

There are lots of concepts we need to grasp in Python. And everyone learns them differently, in different sequences. Here are some things I wish I learnt much earlier when I was still a Python beginner.

1) Tuple Unpacking + Tuple Unpacking With *
person = ['bob', 30, 'male']

name, age, gender = person

# name='bob, age=30, gender='male'
^ we can use tuple unpacking to assign multiple variables at one go.

fruits = ['apple', 'orange', 'pear', 'pineapple', 'durian', 'banana']

first, second, *others = fruits

# first='apple', second='orange'
# others = ['pear', 'pineapple', 'durian', 'banana']
^ we can add * in front of variables to unpack everything else into that variable.

2) List Comprehension + Dict/Set Comprehension
lis = [expression for i in iterable if condition]
l1 = [i for i in range(1,4)]              # [1,2,3]

l2 = [i*2 for i in range(1,4)]            # [2,4,6]

l3 = [i**2 for i in range(1,4)]           # [1,4,9]

l4 = [i for i in range(1,4) if i%2==1]    # [1,3]
^ with list comprehension, we can create a custom list in one line of code.

set1 = {i for i in range(1,4)}          # {1,2,3}

d1 = {i:i**2 for i in range(1,4)}       # {1:1, 2:4, 3:9}
^ set comprehension and dictionary comprehension can be used to create sets and dictionaries in the same way we create lists using list comprehensions.

3) Ternary operator
score = 57
if score > 90:
  grade = 'A*'
elif score > 50:
  grade = 'pass'
else:
  grade = 'fail'

# grade = 'pass'
^ a normal if-elif-else block

score = 57
grade = 'A*' if score>90 else 'pass' if score>50 else 'fail'

# grade = 'pass'
^ we can condense the if-elif-else block into ONE line using the ternary operator.

4) Magic Methods In Python Classes
class Dog():
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def __str__(self):
    return f'Dog(name={self.name}, age={self.age})'

  def __gt__(self, otherDog):
    return self.age > otherDog.age
^ apart from __init__, __str__ and __gt__ are magic methods that allow us to do special things with our Dog objects.

dog = Dog('rocky', 4)
print(dog)    # Dog(name=rocky, age=4)
^ the __str__ magic method defines what is returned when we call str(dog), which is called when we print the dog object.

dog1 = Dog('rocky', 4)
dog2 = Dog('fifi', 2)

print(dog1 > dog2)      # True
^ the __gt__ magic method defines what happens when we compare 2 dogs using the > operator.

5) *args and **kwargs
def test(a, b, *args):
  print(f'{a=} {b=} {args=}')

test(1,2,3,4,5)  # a=1 b=2 args=(3,4,5)
^ *args allow our functions to take in any number of positional arguments (which will be stored in a tuple args)

def test(a, b, **kwargs):
  print(f'{a=} {b=} {kwargs=}')

test(a=1, b=2, c=3, d=4)    # a=1 b=2 kwargs={'c': 3, 'd': 4}
^ **kwargs allow our functions to take in any number of keyword arguments (which will be stored in a dict kwargs)

6) Working with multiple .py files
# helper.py
def test123():
  print('test123 is called')
# main.py
from helper import test123

test123()    # test123 is called
When you get a job as a software engineer, you WILL work on projects with many many many different files. Do get familiar early with how to import functions from other files.

7) if __name__ == ‘__main__’
# helper.py
def test123():
  print('test123 is called')

if __name__ == '__main__':
  # this line only runs if we run helper.py DIRECTLY
  print('print statement from helper.py')
# main.py
from helper import *

test123()    # test123 is called
^ the line if __name__ == '__main__' evaluates to True in a .py file only if we run the .py file directly. We use this line so that we don’t accidentally run lines of code that we don’t intend to run.

8) Truthy & falsy values
# 0 if falsy, and evaluates to False
if 0: print('this wont print')

# non-zero numbers are truthy, and evaluate to True
if 1: print('this prints')
if 2: print('this prints')
if 100: print('this prints')
if -1: print('this prints')
if 3.14: print('this prints')
# empty sequences are falsy, and evaluate to False
if '': print('this wont print')
if []: print('this wont print')
if {}: print('this wont print')
if set(): print('this wont print')

# non-empty sequences are truthy, and evaluate to True
if 'a': print('this prints')
if [1]: print('this prints')
if {2:3}: print('this prints')
if {1,2}: print('this prints')
# None is falsy, and evaluates to False
obj = None
if obj: print('this wont print')

# objects are truthy, and evaluates to True
obj = Dog()
if obj: print('this prints')
9) break vs continue vs pass
for i in [1,2,3,4,5]:
  if i == 3:
    break

  print(i)

# this prints 1 and 2
^ break stops the for/while loop entirely. No other iteration happens.

for i in [1,2,3,4,5]:
  if i == 3:
    continue

  print(i)

# this prints 1, 2, 4 and 5
^ continue skips ONE iteration. Other iterations still happen afterwards.

for i in [1,2,3,4,5]:
  if i == 3:
    pass

  print(i)

# this prints 1, 2, 3, 4 and 5
^ pass does absolutely nothing.

10) try except finally blocks
try:
  # risky code that could cause exceptions

except:
  # this block executes if an exception happens in the try block

finally:
  # stuff here will ALWAYS execute
^ try-except-finally blocks allow us to handle stuff when errors and exceptions happen in our code (instead of just crashing)

11) Python Web API building libraries
If you intend to be a software engineer, chances are that you need to know this quite well. I learnt about this rather late, and wish I was exposed to this much earlier in my coding journey.

Some easy-to-learn libraries in Python:

Python FastAPI — this allows us to build APIs very easily
Python Flask — we can build APIs using Flask too, and even simple web applications
12) Decorators
I learnt about this VERY late in my Python journey, and used to ignore any @decorator syntax that I saw. But it’s better to understand what’s happening in your code.

def add_exclamation_mark(your_function):
  def inner(*args, **kwargs):
    return your_function(*args, **kwargs)
  return inner

@add_exclamation_mark
def greet(name):
  return f'hello {name}'
Decorators are functions that 1) take in another function 2) tweak how the functio works and 3) return another function. When we put @add_exclamation_mark above the greet function, we are actually decorating the greet function, and changing how the greet function works.

# @add_exclamation_mark
# def greet(name)
#
# ^ THIS IS THE SAME AS BELOW:
#
# greet = add_exclamation_mark(greet)

print(greet('tim'))    # hello tim!
^ what happens when we call the decorated greet function. Due to our decorator, our greet function behaves differently, and now has an additional ! after its returned value.

13) Generators + the ‘yield’ Keyword
def simple_generator():
  yield 'apple'
  yield 'orange'
  yield 'pear'

for fruit in simple_generator():
  print(fruit)

# apple orange pear
The yield keyword is like the return keyword. Except that the function does not stop completely after yielding something.

A function that contains the yield keyword becomes a generator function, and can have multiple outputs (the stuff that are yielded).

14) Method chaining
I actually learnt about this much later than I should have.

s = ' APPLE ORANGE PEAR '
s = s.strip()    # s is now 'APPLE ORANGE PEAR'
s = s.lower()    # s is now 'apple orange pear'
s = s.split()    # s is now ['apple', 'orange', 'pear']
^ some generic code to clean a string.

s = ' APPLE ORANGE PEAR '
s = s.strip().lower().split()

# s is now ['apple', 'orange', 'pear']
^ we can chain multiple methods together in one line to save ourselves a few lines of code.

15) Basic machine learning — regression & classification
Before I knew (on a basic level) how machine learning worked, I thought it was some sort of magical magic.

After I learnt how machine learning worked (on a basic level), I was like oh ok so it’s kinda automated statistics with help from a computer. It was no longer magical magic.

Machine learning is a huge huge field, but we usually start with supervised learning — more specifically, classification and regression. As a starter kit, do check out scikit-learn, a Python library that does all the machine learning code for you, and allows you to simply use their functions and classes.

16) Basic Data Structures & Algorithms
After going through countless coding interviews for internships and full-time positions, I realised how important this step is. Most if not all of the coding interviews required the interviewee to be decently competent in this area.

I have unfortunately screwed up quite a few coding interviews at big-name companies just because I didn’t practice enough, which probably cost me quite a few excellent internships.

If you’re interviewing soon or currently, and think that you can wing the interview because you’re good, DON’T. PRACTICE your data structures and algorithms. Take it from someone who made the same mistake years ago.

The earlier you start practicing these coding interview questions, the better you get at them, and the better the opportunities you get.

17) Different data structures & when to use them
Python has a couple of built-in data structures

# ordered collection of elements
list1 = [1,2,3]

# an immutable list. we can use this as a dict key
tuple1 = (1,2,3)

# O(1) when accessing a value using a key
dict1 = {'apple':4, 'orange':5}

# unordered collection containing only unique elements
# O(1) when checking if element exists inside a set
set1 = {1,2,3}

# an immutable set. we can use this as a dict key
frozenset1 = frozenset({1,2,3})
18) Lambda functions
For a long time, I saw a lambda function and went ok I’m gonna ignore that. Until I actually took some time to understand them. And found out how simple it actually was.

def add(x, y):
  return x + y

# this is the same as

add = lambda x,y : x + y
^ lambda functions are simply normal functions, but written using a different syntax. More examples:

def test():
  return 'hello'

# this is the same as 

test = lambda : 'hello'
def test2(a,b,c,d):
  return (a+b) / (c-d)

# this is the same as

test2 = lambda a,b,c,d : (a+b) / (c-d)
19) assert + raise + custom exceptions
assert score <= 100
# ensuring that score cannot be above 100.
^ the assert keyword allows us to conduct a sanity test in the middle of our code. If score > 100, an AssertionError is raised, and our program crashes forcefully.

if score > 100:
  raise Exception('score cannot be higher than 100')
# ensuring that score cannot be above 100.
^ the raise keyword allows us to forcefully cause an Exception (we can customize the message in the Exeption too)

class ScoreException(Exception):
  def __init__(self):
    super().__init__('score cannot be higher than 100')

if score > 100:
  raise ScoreException()
^ we can also create our own Exception types by inheriting from the Exception class.

20) Multiprocessing in Python
The built-in multiprocessing module in Python allows us to run more than 1 function concurrently (at the same time).

import multiprocessing
import time
import datetime

def yourfunction(x):
    start = datetime.datetime.now()
    time.sleep(1)
    end = datetime.datetime.now()
    return f'x={x} start at {start}, end at {end}'

if __name__ == '__main__':
    with multiprocessing.Pool(processes=3) as pool:
        data = pool.map(yourfunction, [1, 2, 3, 4, 5, 6, 7])

    for row in data:
        print(row)
x=1 start at 2023-04-16 13:39:32.035510, end at 2023-04-16 13:39:33.037308
x=2 start at 2023-04-16 13:39:32.035795, end at 2023-04-16 13:39:33.037324
x=3 start at 2023-04-16 13:39:32.037349, end at 2023-04-16 13:39:33.037629
x=4 start at 2023-04-16 13:39:33.037725, end at 2023-04-16 13:39:34.040135
x=5 start at 2023-04-16 13:39:33.037892, end at 2023-04-16 13:39:34.040160
x=6 start at 2023-04-16 13:39:33.037986, end at 2023-04-16 13:39:34.040161
x=7 start at 2023-04-16 13:39:34.040454, end at 2023-04-16 13:39:35.045383
Here, my code runs 3 functions concurrently (each by 1 worker)

yourfunction(1) yourfunction(2) & yourfunction(3) runs at the same time.
yourfunction(4) yourfunction(5) & yourfunction(6) run at the same time also.
yourfunction(7) runs on its own
