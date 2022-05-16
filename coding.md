# Roadmap

- python, java, es6, bash
- comments
- variables
- primitive types
- print
- operators
- types
- strings
- lists
- sets
- maps
- functions
- conditionals
- loops
- classes
- modules
- regular expressions
- files
- json

# Comments

- single line comment  :: # in python, // in java and es6, # in bash
- multi line comment :: ''' or """ in python, /\* \*/ in java and es6, /\*\* \*/ in javadoc, none in bash.


# Variables

- Variable names are case sensitive in python, java, es6 and bash. 
- Python and bash has no semicolon at the end of every statement while java, es6 have it. 
- Python and bash use underscore seperated names as variable name convention. Java and es6 use camelcase.
```python
a = 1
```

```java
int a = 1;
```

```es6
let a = 1;
const a = 1;
```

```bash
a=1    # No space around equal sign.
```


# Primite Types

```python
x = 1                        # int
y = 2.5                      # float
name = 'John'                # str
is_cool = True               # bool
x, y, z = (1, 2.5, 'test')   # multiple assignment
```


# Print

```python
print('Hello World!')
print(x, y, z)               # print can accept multiple arguments.
```

```java
System.out.println("Hello World!");
```

```javascript
console.log('Hello World!');
```

```bash
echo 'Hello World!'
```


# Operators

```python
a = b + c
a = b - c
a = b * c
a = b / c                    # 10 / 3 = 3.33333333
a = b % c                    # -7 % 3 = 2, 7 % -3 = -2, remainders should be on the same side with divisor.
a = b // c
```


# Types

```python
type(3)                      # <class 'int'>
type(1.5)                    # <class 'float'>
type('hello')                # <class 'str'>
type(True)                   # <class 'bool'>
type(('apple', ))            # <class 'tuple'>
type(('apple'))              # <class 'str'>
type(())                     # <class 'tuple'>
type([1, 2, 3])              # <class 'list'>
type({1, 2, 3})              # <class 'set'>
type({'name': 'jeff', 'age': 40})      # <class 'dict'>
```

```javascript
typeof(3)                    // number
typeof(1.5)                  // number
typeof('hello')              // string
```


# Castings

```python
a = str(1)                   # to string
a = int(1.5)                 # to int
a = float(1)                 # to float
```


# Strings

- concat
- format
- methods

```python
'foo' + 'bar'               # Use + to concat.
'foo' + 37                  # Error! Different types of data cannot concat, use str() instead.
'foo' + str(37)
print('My name is {name}, and I am {age}.'.format(name='Jeff', age=41))
print(f'My name is {name}, and I am {age}.')     # fstring appears on python 3.6+.
len(s)
s.find('r')
s.split()
s.replace('foo', 'bar')
s.startswith('foo')
s.endswith('foo')
s.upper()
s.lower()
s.capitalize()
s.count('h')
s.isalnum()
s.isalpha()
s.isnumeric()
```


# Lists

In python, a tuple is an unchangeable list.

- list creation
- get value
- get length
- add value
- delete value
- change value
- reverse list
- sort list

```python
fruits = ['apple', 'banana', 'orange', 'pear', 'melon']
numbers = list((1, 2, 3, 4, 5))
numbers[0]
len(numbers)
fruits.append('mango')
fruits.insert(2, 'cherry')
fruits.remove('mango')
fruits.pop(2)
fruits[0] = 'strawberry'
fruits.reverse()             # fruits changed to reverse order, not generating a new one.
fruits.sort()
fruits.sort(reverse=True)

tools = ('rocket', 'bus', 'plane', 'bike', 'car')          # tuple creation
numbers = tuple((1, 2, 3, 4, 5))
fruits = ('apple', )         # In order to create a tuple, you have to add a comma if you have only one element. Otherwise, you will only get a string.
del fruits                   # Delete tuple completely.
```


# Sets

- set creation
- check existence
- crud value

```python
fruits = {'apple', 'banana', 'orange', 'pear', 'melon'}
print('apple' in fruits)
fruits.add('grape')
fruits.remove('grape')
fruits.clear()
del fruits
```

# Maps

In python, map is called dict.

- create a map
- crud value
- copy a map

```python
person = {'first_name': 'Jeff', 'last_name': 'Huang', 'email': 'wearehw3a@gmail.com', 'age': 41}
person = dict(first_name='Jeff', last_name='Huang', email='wearehw3a@gmail.com', age=41)
person['first_name']
person.get('email')
person['mobile'] = '18621553968'
person.pop('mobile')
del(person['age'])
person.keys()
person.items()
person.clear()
len(person)
person2 = person.copy()
```


# Functions

- create a function
- call a function
- return value
- lambda function

```python3
def say_hello(name = 'James'):
  print(f'hello, {name}')
  return 'Done'

say_hello('Jeff')

get_sum = lamda num1, num2 : num1 + num2         # lambda function
```


# Conditionals

- and, or, not
- in, not in
- is, is not

```python3
if x > y:
  foo()
elif x == y:
  baz()
else:
  bar()

if x not in fruits:
  print(x)
```


# Loops

- for loop
- while loop
- break
- range

```python3
for person in people:
  if person == 'Jeff':
    break
  elif person == 'Andy':
    continue
  print(person)

for i in range(0, 11):       # Print 1-10, not included 11.
  print(i)

while count <= 10:
  count += 1
```

# Classes

In python, almost everything is an object.

- create a class
- create an object
- extend a class

```python3
class User:
  def __init__(self, name):
    self.name = name

jeff = User('Jeff')
print(jeff.name)

class Dog(Animal):
```


# Modules

In python, a module is a file.

```python3
import datetime
from datetime import date
import time

today = datetime.date.today()
timestamp = time.time()
```


# Regular Expressions

```python3
import re
  
re.match("^.+@(\[?)[a-zA-Z0-9-.]+.([a-zA-Z]{2,3}|[0-9]{1,3})(]?)$", email)
```


# Files

```python3
my_file = open('foo.txt', 'w')
my_file = open('foo.txt', 'r+')
my_file.write('hello')                 # no new line
text = my_file.read(100)
my_file.close()
my_file = open('foo.txt', 'a')         # append mode

print(my_file.name)
print(my_file.closed)
print(my_file.mode)
```


# Json

```python3
import json

user_json = '{"first_name": "Jeff", "last_name": "Huang", "age": 30}'
user = json.loads(user_json)
foo_json = json.dumps(user)
```
