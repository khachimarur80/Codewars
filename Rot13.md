# Rot13 [5 kyu]

[See Problem](https://www.codewars.com/kata/530e15517bc88ac656000716)

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

Please note that using `encode` is considered cheating.

## Solution 

### Python

```
def rot13(message):
    alphabet = 'abcdefghijklmnopqrstuvwxyz'
    encoded = ''
    for char in message:
        if char.isalpha():
            if char.islower():
                encoded += alphabet[(alphabet.index(char)+13)%26]
            else:
                encoded += alphabet[(alphabet.index(char.lower())+13)%26].upper()
        else:
            encoded += char
    return encoded
```

### C++

```
#include <string>
using namespace std;

string rot13(string msg)
{
  string alphabet = "abcdefghijklmnopqrstuvwxyz";
  string encoded;
  int msgLength = msg.length();
  for(int i=0; i<msgLength; i++) {
    bool isLower = false;
    bool isUpper = false;
    int index;
    for (int j=0; j<26; j++) {
      if (toupper(alphabet[j])==msg[i]) {
        isUpper = true;
        index = j;
        break;
      }
      else if (alphabet[j]==msg[i]) {
        isLower = true;
        index = j;
        break;
      }
    }
    if (isLower) {
      encoded += alphabet[(index+13)%26];
    }
    else if (isUpper) {
      encoded += toupper(alphabet[(index+13)%26]);
    }
    else {
      encoded += msg[i];
    }
  }
  return encoded;
}

```