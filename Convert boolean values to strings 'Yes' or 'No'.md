# Convert boolean values to strings 'Yes' or 'No'. [8 kyu]

[See Problem](https://www.codewars.com/kata/53369039d7ab3ac506000467)

Complete the method that takes a boolean value and return a `"Yes"` string for `true`, or a `"No"` string for false.

## Solution

```
#include <string>

std::string bool_to_word(bool value)
{
  if (value) {
    return "Yes";
  }
  return "No";
}
```