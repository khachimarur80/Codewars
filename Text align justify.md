# Text align justify [4 kyu]

[See Problem](https://www.codewars.com/kata/537e18b6147aa838f600001b)

Your task in this Kata is to emulate text justification in monospace font. You will be given a single-lined text and the expected justification width. The longest word will never be greater than this width.

Here are the rules:

- Use spaces to fill in the gaps between words.
- Each line should contain as many words as possible.
- Use '\n' to separate lines.
- Gap between words can't differ by more than one space.
- Lines should end with a word not a space.
- '\n' is not included in the length of a line.
- Large gaps go first, then smaller ones ('Lorem--ipsum--dolor--sit-amet,' (2, 2, 2, 1 spaces)).
- Last line should not be justified, use only one space between words.
- Last line should not contain '\n'
- Strings with one word do not need gaps ('somelongword\n').


Example with width=30:
```
Lorem  ipsum  dolor  sit amet,
consectetur  adipiscing  elit.
Vestibulum    sagittis   dolor
mauris,  at  elementum  ligula
tempor  eget.  In quis rhoncus
nunc,  at  aliquet orci. Fusce
at   dolor   sit   amet  felis
suscipit   tristique.   Nam  a
imperdiet   tellus.  Nulla  eu
vestibulum    urna.    Vivamus
tincidunt  suscipit  enim, nec
ultrices   nisi  volutpat  ac.
Maecenas   sit   amet  lacinia
arcu,  non dictum justo. Donec
sed  quam  vel  risus faucibus
euismod.  Suspendisse  rhoncus
rhoncus  felis  at  fermentum.
Donec lorem magna, ultricies a
nunc    sit    amet,   blandit
fringilla  nunc. In vestibulum
velit    ac    felis   rhoncus
pellentesque. Mauris at tellus
enim.  Aliquam eleifend tempus
dapibus. Pellentesque commodo,
nisi    sit   amet   hendrerit
fringilla,   ante  odio  porta
lacus,   ut   elementum  justo
nulla et dolor.
```

Also you can always take a look at how justification works in your text editor or directly in HTML (css: text-align: justify).

Have fun :)

## Solution

```
import re
def justify(text, width):
    lines = []
    base_text = text.replace('.', '. ')
    words = list(filter(lambda x: len(x), base_text.split(' ')))
    curr_words = ''
    line = []
    #Split the text in adecuate lines
    for word in words:
        if len(line):
            if sum([len(i) for i in line])+len(word) + len(line) > width:
                curr_words = word
                lines.append(line)
                line = [word]
            else:
                curr_words += word
                line.append(word)
        else:
            curr_words += word
            line.append(word)
    if line:
        lines.append(line)

    #Merge the lines in adecuate text
    result_text = []
    for line in lines[:-1]:
        spaces = width-sum([len(w) for w in line])
        index = 0
        if len(line)>1:
            while spaces>0:
                line[index%(len(line)-1)] = line[index%(len(line)-1)]+' '
                index += 1
                spaces -= 1
                
        result_text.append(''.join(line))
        
    return '\n'.join(result_text)+'\n'+' '.join(lines[-1])
```