# Reversed Strings [8 kyu]

[See Problem](https://www.codewars.com/kata/5168bb5dfe9a00b126000018)

Complete the solution so that it reverses the string passed into it.

```
'world'  =>  'dlrow'
'word'   =>  'drow'
```

## Solutions

```
#include <string>
using namespace std ; 

string reverseString (string str )
{
  string result;
  for (int i=str.length()-1; i>=0; i--) {
    result += str[i];
  }
  
  return result;
}
```