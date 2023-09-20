# String incrementer [5 kyu]

[See Problem](https://www.codewars.com/kata/54a91a4883a7de5d7800009c)

Your job is to write a function which increments a string, to create a new string.

- If the string already ends with a number, the number should be incremented by 1.
- If the string does not end with a number. the number 1 should be appended to the new string.

Examples:

`foo -> foo1`

`foobar23 -> foobar24`

`foo0042 -> foo0043`

`foo9 -> foo10`

`foo099 -> foo100`

_Attention: If the number has leading zeros the amount of digits should be considered._

## Solutions

```
#include <string>

std::string incrementString(const std::string &str)
{
  std::string numbers = "0123456789";
  std::string number_part = "";
  std::string string_part = "";
  bool no_str = true;
  
  int letterCount = str.length();
  
  for (int i=letterCount-1; i>=0; i--) {
    bool is_num = false;
    for (int j=0; j<10; j++) {
      if (numbers[j]==str[i]) {
        is_num = true;
        break;
      }
    }
    if (is_num && no_str) {
      number_part = str[i] + number_part;
    }
    else {
      no_str = false;
      string_part = str[i] + string_part;
    }
  }
  int number_up;
  if (number_part=="") {
    number_up = 1;
  }
  else {
    number_up = std::stoi(number_part)+1; 
  }
  
  std::string result = string_part;
  int len_diff = number_part.length() - std::to_string(number_up).length();
  
  for (int i=0; i<len_diff; i++) {
    result += "0";
  }
  result += std::to_string(number_up);
  return result;
}
```