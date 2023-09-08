# First non-repeating character [5 kyu]

[See Problem] (https://www.codewars.com/kata/52bc74d4ac05d0945d00054e)

Write a function named `first_non_repeating_letter` that takes a string input, and returns the first character that is not repeated anywhere in the string.

For example, if given the input `'stress'`, the function should return `'t'`, since the letter t only occurs once in the string, and occurs first in the string.

As an added challenge, upper- and lowercase letters are considered the same character, but the function should return the correct case for the initial letter. For example, the input `'sTreSS'` should return `'T'`.

If a string contains all repeating characters, it should return an empty string (`""`) or `None` -- see sample tests.

## My Solution

```
def first_non_repeating_letter(s):
    o_s = s
    s = s.lower()
    letters = sorted([c for c in list(set(s)) if s.count(c)==1], key=lambda x:s.index(x))
    if letters:
        return o_s[s.index(letters[0])]
    else:
        return ''
```
