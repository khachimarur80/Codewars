# Binary Addition [7 kyu]

[See Problem](https://www.codewars.com/kata/551f37452ff852b7bd000139)

Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition.

The binary number returned should be a string.

Examples:(Input1, Input2 --> Output (explanation)))




## Solutions

### My attempt

```
#include <cstdint>
#include <string>
#include <math.h>
#include <stdio.h>
using namespace std;

string add_binary(uint64_t a, uint64_t b) {
  int remainder = a+b;
  string result = "";
  int lastVisited = 0;

  while (remainder>0) {
    int power = log(remainder)/log(2);
    remainder -= pow(2, power);
    
    if (result=="") {
      result += "1";
      lastVisited = power;
    }
    else {
      for (int i=0; i<(lastVisited-power-1); i++) {
        result += "0";
      }
      lastVisited = power;
      result += "1";
    }
  }
  
  for (int i=0; i<lastVisited; i++) {
    result += "0";
  }
  
  return result;
}
```

### ChatGPT correction

I shouldn't use log and pow

```
#include <cstdint>
#include <string>
#include <iostream>

using namespace std;

string add_binary(uint64_t a, uint64_t b) {
    uint64_t sum = a + b;
    string result = "";
    
    if (sum == 0) {
        return "0";
    }

    while (sum > 0) {
        int bit = sum % 2;
        result = to_string(bit) + result;
        sum /= 2;
    }

    return result;
}
```