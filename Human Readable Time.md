# Human Readable Time [5 kyu]

[See Problem](https://www.codewars.com/kata/52685f7382004e774f0001f7)

Write a function, which takes a non-negative integer (seconds) as input and returns the time in a human-readable format (HH:MM:SS)

- `HH = hours, padded to 2 digits, range: 00 - 99
- `MM` = minutes, padded to 2 digits, range: 00 - 59
- `SS` = seconds, padded to 2 digits, range: 00 - 59
The maximum time never exceeds 359999 (`99:59:59)

You can find some examples in the test fixtures.

## Solution

```
def make_readable(seconds):
    hours = seconds//3600
    seconds -= hours*3600
    minutes = seconds//60
    seconds -= minutes*60
    return f"{hours:02d}:{minutes:02d}:{seconds:02d}"
    
```