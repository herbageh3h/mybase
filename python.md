# Python
## Quick Start

```
python -m venv env
source env/bin/activate

pip list
pip install flake8

flake8 dirtool.py
```

## FAQ

### 1. How to convert str to bytes?

```
ss.encode('utf-8')
bytes(ss, 'utf-8')
```

## Regular Expression
### meta characters (14)
```
. * + ? ^ $ | ( ) [ ] { } \
```
### meta classes
```
\d => [0-9]
\D => [^0-9]
\s => [ \t\n\r\f\v]
\S => [^ \t\n\r\f\v]
\w => [a-zA-Z0-9_]
\W => [^a-zA-Z0-9_]
```
## Scripts
### Command Line Arguments Parser
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
### File reading and writing
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
## str
```
print(fruit.strip())
```
## list
```
fruits.sort()

l2 = l1[:]
```
## print
```
fruits = ['apple', 'banana', 'orange']
print(*fruits, sep=',')

print('Hello, World', end='!')
```

## Tools
### Flake8
```
flake8 dirtool.py
```
- [flake8 rules]("https://www.flake8rules.com/")
### pip
```
pip --version
pip list
python -m pip install --upgrade pip
```
