# Split Strings [6 kyu]

[See Problem]()

Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('\_').

Examples:
```
* 'abc' =>  ['ab', 'c_']
* 'abcdef' => ['ab', 'cd', 'ef']
```

## Solutions

```
def solution(s):
    s = s+'_' if len(s)%2!=0 else s
    return [s[i:i+2] for i in range(0,len(s),2)]
```