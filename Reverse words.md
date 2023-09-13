# Reverse words [7 kyu]

[See Problem](https://www.codewars.com/kata/5259b20d6021e9e14c0010d4)

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

## Examples
```
"This is an example!" ==> "sihT si na !elpmaxe"
"double  spaces"      ==> "elbuod  secaps"
```
## Solution
```
#include <string>

std::string reverse_word(std::string str) {
  int len = str.length();
  std::string word;
  for (int i = len - 1; i >= 0; i--) {
    word += str[i];
  }
  return word;
}

std::string reverse_words(std::string str)
{
  int len = str.length();
  std::string result;
  std::string buffer;
  for (int i = 0; i<len; i++) {
    if (str[i]==' ') {
      result += reverse_word(buffer) + ' ';
      buffer.clear();
    }
    else {
      buffer += str[i];
    }
  }
  if (result.length()) {
    return result+reverse_word(buffer);
  }
  return reverse_word(buffer);
}
```