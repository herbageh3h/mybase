# Quick Start

```
python -m venv env
source env/bin/activate

pip list
pip install flake8
pip install --upgrade flake8

python -m pdb demo.py
```
Use black to format your code.

Use flake8 to check your code.


# FAQ

## How to convert str to bytes?

```
ss.encode('utf-8')
bytes(ss, encoding='utf-8')
```

## How to deal with time?

```
from datetime import datetime as dt

s = '21 June, 2018'
dt.strptime(s, '%d %B, %Y)

d1 = dt.now()
print(d1.strftime('%Y-%m-%d %H:%M:%S'))

import datetime

delta = datetime.timedelta(days=1)
print(int(delta.total_seconds()))
```

* %d: day of the month with padding zero. eg. 01, 02, 31
* %-d: day of the month as number. eg. 1, 2, 31
* %B: month name full. eg. June, January
* %b: month name abbr. eg. Jan, Feb
* %Y: year. eg. 2018, 2021
* %m: month with padding zero. eg. 01, 12
* %-m: month as number. eg. 1, 12
* %H: hour. eg. 01, 15, 23
* %M: minute. eg. 01, 59
* %S: second. eg. 02, 38
* %a: weekday name abbr. eg. Sun, Mon
* %A: weekday full name. eg. Sunday, Monday
* %w: weekday as number. eg. 0, 1, 6
* %z: timezone in utc offset. eg. -0000, +0530, -7000

## How to deal with unicode?

```
ord(u'$')
chr(176)
```

## How to deal with ModuleNotFoundError?

On windows, set environment variable.

```
set PYTHONPATH = "."
```

## How to build and install?

```
python setup.py build
python setup.py install
```

# Regular Expression

## meta characters (14)

```
. * + ? ^ $ | ( ) [ ] { } \
```

## meta classes

```
\d => [0-9]
\D => [^0-9]
\s => [ \t\n\r\f\v]
\S => [^ \t\n\r\f\v]
\w => [a-zA-Z0-9_]
\W => [^a-zA-Z0-9_]
```

# Scripts

## Command Line Arguments Parser

```
import argparse

parser = argparse.ArgumentParser()

parser.add_argument('path', type = str)
parser.add_argument('--search', type=str, help='regular expression to filter file names')
parser.add_argument('--times', type = int)

args = parser.parse_args()

path = args.path
search = args.search
times = args.times
```

## File reading and writing

```
import os

path = os.path.expanduser('~/tmp/fruit')
with open(path) as f1:
    fruits = f1.readlines()

fruits.sort()
with open(os.path.join(os.path.dirname(path), 'fruit_sorted'), 'wt') as f2
    for fruit in fruits:
        print(fruit.strip(), file=f2)
```

# str

```
print(fruit.strip())
```

# list

```
fruits.sort()

l2 = l1[:]
```

# print

```
fruits = ['apple', 'banana', 'orange']
print(*fruits, sep=',')

print('Hello, World', end='!')
```

# Keywords

- True
- False
- None
- class
- def
- return
- if
- elif
- else
- and
- or
- not
- is
- while
- for
- in
- break
- continue
- with
- from
- import
- as
- try
- except
- finally
- raise
- lambda
- pass
- yield
- del
- assert
- global
- nonlocal

# Tools

## Flake8

```
flake8 dirtool.py
```
- [flake8 rules]("https://www.flake8rules.com/")

## pip

```
pip --version
pip list
python -m pip install --upgrade pip
pip install --upgrade flake8
pip freeze
```

# pdb

```
python -m pdb demo.py
```

## pdb commands

* q: quit
* p: print
* ll: show the current scope source
* pp: pretty print
* b: breakpoint, eg. b 18, b demo_func, use just b to list all breakpoints
* c: continue
* n: step over
* s: step into
* enable 1: enable breakpoint #1
* disable 1: disable breakpoint #1
* cl: delete breakpoint
* unt: until
* display: continue showing expression value
* w: print call stack
* h: help

# Links

- [Understanding Object Instantiation and Metaclasses in Python](https://www.honeybadger.io/blog/python-instantiation-metaclass/)
