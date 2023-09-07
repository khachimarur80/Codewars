# Alphabetic Anagram [3 kyu]

[See problem](https://www.codewars.com/kata/53e57dada0cb0400ba000688)

Consider a "word" as any sequence of capital letters A-Z (not limited to just "dictionary words"). For any word with at least two different letters, there are other words composed of the same letters but in a different order (for instance, STATIONARILY/ANTIROYALIST, which happen to both be dictionary words; for our purposes "AAIILNORSTTY" is also a "word" composed of the same letters as these two).

We can then assign a number to every word, based on where it falls in an alphabetically sorted list of all words made up of the same group of letters. One way to do this would be to generate the entire list of words and find the desired one, but this would be slow if the word is long.

Given a word, return its number. Your function should be able to accept any word 25 letters or less in length (possibly with some letters repeated), and take no more than 500 milliseconds to run. To compare, when the solution code runs the 27 test cases in JS, it takes 101ms.

For very large words, you'll run into number precision issues in JS (if the word's position is greater than 2^53). For the JS tests with large positions, there's some leeway (.000000001%). If you feel like you're getting it right for the smaller ranks, and only failing by rounding on the larger, submit a couple more times and see if it takes.

Python, Java and Haskell have arbitrary integer precision, so you must be precise in those languages (unless someone corrects me).

C# is using a long, which may not have the best precision, but the tests are locked so we can't change it.

Sample words, with their rank:
ABAB = 2
AAAB = 1
BAAA = 4
QUESTION = 24572
BOOKKEEPER = 10743

## My attempt (07/09/23)

```
import numpy as np

def perm_count(lst):
    total = np.math.factorial(len(lst))
    div = 1
    for item in set(lst):
        div *= np.math.factorial(lst.count(item))
    return total//div

def list_position(word):
    model = dict(sorted({char: word.count(char) for char in word}.items()))
    chars = sorted(list(set(word)))
    pos = 1
    index = 0
    for char in word:
        if char!=chars[0]:
            seen = [chars[0]]
            s_word = ''.join([i * (model[i] if not i in seen else model[i] - 1) for i in model])
            pos += chars.index(char)*perm_count(s_word)
            model[char] -= 1
            if model[char]==0:
                chars = list(filter(lambda x: x!= char, chars))
        else:
            model[char] -= 1
            if model[char]==0:
                chars = chars[1:]
        index += 1
    return pos
```

## Corrected with ChatGPT because I wasn't handling correctly duplicate letters

```            
            

import math

def perm_count(char_counts):
    total = math.factorial(sum(char_counts.values()))
    div = 1
    for count in char_counts.values():
        div *= math.factorial(count)
    return total // div

def list_position(word):
    char_counts = dict(sorted({char: word.count(char) for char in word}.items()))
    sorted_word = ''.join(sorted(word))
    chars = sorted(list(set(word)))
    pos = 1
    index = 0
    for char in word:
        for other_char in char_counts:
            if other_char < char:
                char_counts[other_char] -= 1
                pos += perm_count(char_counts)
                char_counts[other_char] += 1

        char_counts[char] -= 1
        if char_counts[char]==0:
            del char_counts[char]
        index += 1
        
    return pos
```


