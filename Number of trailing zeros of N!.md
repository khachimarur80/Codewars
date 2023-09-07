# Number of trailing zeros of N! [5 kyu]

[See problem](https://www.codewars.com/kata/52f787eb172a8b4ae1000a34)

Write a program that will calculate the number of trailing zeros in a factorial of a given number.

```
N! = 1 * 2 * 3 *  ... * N
```

Be careful 1000! has 2568 digits...

For more info, see: [Wolfram Factorial](http://mathworld.wolfram.com/Factorial.html)

## Examples

```
zeros(6) = 1
# 6! = 1 * 2 * 3 * 4 * 5 * 6 = 720 --> 1 trailing zero

zeros(12) = 2
# 12! = 479001600 --> 2 trailing zeros
```
_Hint: You're not meant to calculate the factorial. Find another way to find the number of zeros._


```
function zeros (n) {
  let zeros = 0;
  let num = n;
  while (num>=5) {
    zeros += Math.floor(num / 5)
    num = Math.floor(num / 5)
  }
  return zeros
}
```