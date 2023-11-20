# Convert A Hex String To RGB [5 kyu]

[See Problem](https://www.codewars.com/kata/5282b48bb70058e4c4000fa7)

When working with color values it can sometimes be useful to extract the individual red, green, and blue (RGB) component values for a color. Implement a function that meets these requirements:

Accepts a case-insensitive hexadecimal color string as its parameter (ex. `"#FF9933"` or `"#ff9933"`)
Returns a Map<String, int> with the structure `{r: 255, g: 153, b: 51}` where r, g, and b range from 0 through 255
Note: your implementation does not need to support the shorthand form of hexadecimal notation (ie `"#FFF"`)

## Example

```
"#FF9933" --> {r: 255, g: 153, b: 51}
```

## Solution

```
function hexToDec(hex) {
  let digits = "0123456789abcdef"
  let val = 0
  for (let i=0; i<hex.length; i++) {
    let digit = hex[hex.length-1-i]
    val += digits.indexOf(digit.toLowerCase())*(16**i)
  }
  return val
}
function hexStringToRGB(hexString) {
  let rVal = hexToDec(hexString.slice(1,3))
  let gVal = hexToDec(hexString.slice(3,5))
  let bVal = hexToDec(hexString.slice(5,7))
  return { r: rVal, g: gVal, b: bVal}
}
```