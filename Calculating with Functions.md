# Calculating with Functions [5 kyu]

[See Problem](https://www.codewars.com/kata/525f3eda17c7cd9f9e000b39)

This time we want to write calculations using functions and get the results. Let's have a look at some examples:
```
seven(times(five())) # must return 35
four(plus(nine())) # must return 13
eight(minus(three())) # must return 5
six(divided_by(two())) # must return 3
```
Requirements:

- There must be a function for each number from 0 ("zero") to 9 ("nine")
- There must be a function for each of the following mathematical operations: plus, minus, times, divided_by
- Each calculation consist of exactly one operation and two numbers
- The most outer function represents the left operand, the most inner function represents the right operand
- Division should be integer division. For example, this should return `2`, not `2.666666...`:

`eight(divided_by(three()))

## Solution

```
def zero(x=None):
    if x:
        return eval('0'+x)
    return 0
def one(x=None):
    if x:
        return eval('1'+x)
    return 1
def two(x=None):
    if x:
        return eval('2'+x)
    return 2
def three(x=None):
    if x:
        return eval('3'+x)
    return 3
def four(x=None):
    if x:
        return eval('4'+x)
    return 4
def five(x=None): 
    if x:
        return eval('5'+x)
    return 5
def six(x=None):
    if x:
        return eval('6'+x)
    return 6
def seven(x=None):
    if x:
        return eval('7'+x)
    return 7
def eight(x=None):
    if x:
        return eval('8'+x)
    return 8
def nine(x=None): 
    if x:
        return eval('9'+x)
    return 9

def plus(x):
    return '+'+str(x)
def minus(x):
    return '-'+str(x)
def times(x):
    return '*'+str(x)
def divided_by(x):
    return '//'+str(x)
```