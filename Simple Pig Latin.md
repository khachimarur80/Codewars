# Simple Pig Latin [5 kyu]

Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

## Examples

```
pig_it('Pig latin is cool') # igPay atinlay siay oolcay
pig_it('Hello world !')    
```

## Solution

```
def pig_it(text):
    return ' '.join([w[1:]+w[0]+'ay' if w.isalpha() else w for w in text.split(' ')])
```