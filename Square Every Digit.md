# Square Every Digit [7 kyu]

[See Problem](https://www.codewars.com/kata/546e2562b03326a88e000020)

Welcome. In this kata, you are asked to square every digit of a number and concatenate them.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1. (81-1-1-81)

Example #2: An input of 765 will/should return 493625 because 72 is 49, 62 is 36, and 52 is 25. (49-36-25)

**Note**: The function accepts an integer and returns an integer.

Happy Coding!

## Solution

```
#include <math.h>
#include <stdio.h>

int square_digits(int num) {
  std::string result;
  
  int len = log(num)/log(10);
  
  for (int i=len; i>=0; i--) {
    int digit = num/pow(10, i);
    num = num - digit*pow(10, i);
    result += std::to_string(digit*digit);
  }
  
  return stoi(result);
}
```