# Moving Zeros To The End [5 kyu]

[See Problem](https://www.codewars.com/kata/52597aa56021e91c93000cb0)

Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

`move_zeros([1, 0, 1, 2, 0, 1, 3]) # returns [1, 1, 2, 1, 3, 0, 0]`

## Solution

```
def move_zeros(lst):
    nums = list(filter(lambda x: x!=0, lst))
    return list(filter(lambda x: x!=0, lst))+[0]*(len(lst)-len(nums))
```
