# Sum Strings as Numbers [4 kyu]

[See Problems](https://www.codewars.com/kata/5324945e2ece5e1f32000370)

Given the string representations of two integers, return the string representation of the sum of those integers.

For example:

```
sumStrings('1','2') // => '3'
```

A string representation of an integer will contain no characters besides the ten numerals "0" to "9".

I have removed the use of `BigInteger` and `BigDecimal` in java

Python: your solution need to work with huge numbers (about a milion digits), converting to int will not work.

```
def sum_strings(x, y):
    max_length = max(len(x), len(y))
    result = ['0']*(max_length+1)
    carry = 0
    for i in range(1, max_length+1):
        if i <= len(x):
             x_digit = int(x[-i]) 
        else: 
            x_digit = 0
        if i <= len(y):
            y_digit = int(y[-i]) 
        else: 
            y_digit = 0

        addition = x_digit + y_digit + carry
        carry = addition // 10
        result[-i] = str(addition % 10)
    
    if carry:
        result[0] = str(carry)
        
    if len(result)>1:
        while result[0]=='0' and len(result)>1:
            result.pop(0)
    
    return ''.join(result) or '0'

```