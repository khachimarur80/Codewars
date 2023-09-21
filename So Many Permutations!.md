# So Many Permutations! [4 kyu]

[See Problem](https://www.codewars.com/kata/5254ca2719453dcc0b00027d)

In this kata, your task is to create all permutations of a non-empty input string and remove duplicates, if present.

Create as many "shufflings" as you can!

Examples:

```
With input 'a':
Your function should return: ['a']

With input 'ab':
Your function should return ['ab', 'ba']

With input 'abc':
Your function should return ['abc','acb','bac','bca','cab','cba']

With input 'aabb':
Your function should return ['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']
```

Note: The order of the permutations doesn't matter.

Good luck!

## Solution

```
def permutations(s):
    available = list(set(s))
    while len(available[0])<len(s):
        remaining = s
        for x in available[0]:
            remaining = remaining.replace(x, '', 1)
        for j in remaining:
            available.append(available[0]+j)
        if remaining:
            available.pop(0)
    return set(available)

```