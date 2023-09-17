# Rot13 [5 kyu]

[See Problem](https://www.codewars.com/kata/530e15517bc88ac656000716)

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

Please note that using `encode` is considered cheating.

## Solution 

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