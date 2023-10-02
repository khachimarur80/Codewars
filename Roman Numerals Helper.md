# Roman Numerals Helper [4 kyu]

[See Problem](https://www.codewars.com/kata/51b66044bce5799a7f000003)

Write two functions that convert a roman numeral to and from an integer value. Multiple roman numeral values will be tested for each function.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Input range : `1 <= n < 4000

In this kata 4 should be represented as IV, NOT as IIII (the "watchmaker's four").

## Examples

```
to roman:
2000 -> "MM"
1666 -> "MDCLXVI"
1000 -> "M"
 400 -> "CD"
  90 -> "XC"
  40 -> "XL"
   1 -> "I"

from roman:
"MM"      -> 2000
"MDCLXVI" -> 1666
"M"       -> 1000
"CD"      -> 400
"XC"      -> 90
"XL"      -> 40
"I"       -> 1
```

## Help

| Symbol | Value |
|--------|-------|
|   I    |   1   |
|   IV   |   4   |
|   V    |   5   |
|   X    |  10   |
|   L    |  50   |
|   C    | 100   |
|   D    | 500   |
|   M    |1000   |


## Solution

```
class RomanNumerals:
    @staticmethod
    def to_roman(val : int) -> str:
        def toRoman(num, letters):
            if num <= 3:
                return num*letters[0]
            elif num==4:
                return letters[0]+letters[1]
            elif num!=9:
                return letters[1]+(num-5)*letters[0]
            else:
                return letters[0]+letters[2]
        def intToRoman(num):
            thousands = num//1000
            hundreds = (num%1000)//100
            tenths = ((num%1000)%100)//10
            units = ((num%1000)%100)%10

            thousands = toRoman(thousands, 'MKK')
            hundreds = toRoman(hundreds, 'CDM')
            tenths = toRoman(tenths, 'XLC')
            units = toRoman(units, 'IVX')

            return(thousands+hundreds+tenths+units)

        return intToRoman(val)

    @staticmethod
    def from_roman(roman_num : str) -> int:
        values = {
            'I' : 1,
            'V' : 5,
            'X' : 10,
            'L' : 50,
            'C' : 100,
            'D' : 500,
            'M' : 1000,
        }
        value = 0
        for i in range(0, len(roman_num)-1):
            if values[roman_num[i]]>=values[roman_num[i+1]]:
                value += values[roman_num[i]]
            else:
                value -= values[roman_num[i]]
                
        return value + values[roman_num[-1]]
```