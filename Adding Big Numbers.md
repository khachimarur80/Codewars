# Adding Big Numbers [4 kyu]

[See Problem](https://www.codewars.com/kata/525f4206b73515bffb000b21)

We need to sum big numbers and we require your help.

Write a function that returns the sum of two numbers. The input numbers are strings and the function must return a string.

## Example
```
add("123", "321"); -> "444"
add("11", "99");   -> "110"
```
## Notes

- The input numbers are big.
- The input is a string of only digits
- The numbers are positives

## Solution

```
function add(a, b) {
  let maxLength = Math.max(a.length, b.length)-1;
  result = ''
  carry = 0
  for (let i=0; i<=maxLength; i++) {
    a_int = parseInt(a[a.length-1-i])
    if (!a_int) {
      a_int = 0
    }
    b_int = parseInt(b[b.length-1-i])
    if (!b_int) {
      b_int = 0
    }
    addition = a_int+b_int+carry
    if (carry!=0) {
      carry = 0
    }
    if (addition>9) {
      addition -= 10
      carry += 1
    }
    result = addition.toString()+result
  }
  if (carry) {
    return '1'+result
  }
  return result
}
```