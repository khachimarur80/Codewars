# Convert string to camel case [6 kyu]

[See Problem](https://www.codewars.com/kata/517abf86da9663f1d2000003)

Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case). The next words should be always capitalized.

Examples
`"the-stealth-warrior"` gets converted to `"theStealthWarrior"`

`"The_Stealth_Warrior"` gets converted to `"TheStealthWarrior"`

`"The_Stealth-Warrior"` gets converted to `"TheStealthWarrior"`

## Solution

```
#include <string>
using namespace std;

string to_camel_case(string text) {
  string output;
  string curr;
  if (text.length() >= 1) {
    for (int i = 0; i<text.length(); i++) {
      if (text[i]!='_'&&text[i]!='-') {
        if (curr.length()==0 && output.length()>0) {
          curr += toupper(text[i]);
        }
        else {
          curr += text[i];
        }
      }
      else {
        output += curr;
        curr.clear();
      }
    }
    return output+curr;
  }
  else {
    return "";
  }
}
```