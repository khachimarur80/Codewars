# RGB To Hex Conversion [5 kyu]

[See problem](https://www.codewars.com/kata/513e08acc600c94f01000001)

The rgb function is incomplete. Complete it so that passing in RGB decimal values will result in a hexadecimal representation being returned. Valid decimal values for RGB are 0 - 255. Any values that fall out of that range must be rounded to the closest valid value.

Note: Your answer should always be 6 characters long, the shorthand with 3 will not work here.

```
Examples (input --> output):
255, 255, 255 --> "FFFFFF"
255, 255, 300 --> "FFFFFF"
0, 0, 0       --> "000000"
148, 0, 211   --> "9400D3"
```

```
function getBaseLog(x, y) {
  return Math.log(y) / Math.log(x);
}
function hexLetter(n) {
  let dict = 'ABCDEF'
  if (n>9) {
    return dict[n-10]
  }
  else {
    return n.toString()
  }
}
function decToHex(n) {
  let digits = [];
  let hex = [];
  let num = n;
  let length = Math.floor(getBaseLog(16, num));
  if (n>255) {
    return 'FF'
  }
  else if (n<=0) {
    return '00'
  }
  else {
    for (let i=length; i>=0; i--) {
      digits.push(
        Math.floor(num/(16**i))
      )
      num -= digits.slice(-1)*(16**i)
    }
    for (let i=0; i<digits.length; i++) {
      hex.push(hexLetter(digits[i]))
    }
    if (hex.length==1) {
     return '0'+hex.join('') 
    }
    else {
      return hex.join('')
    }
  }
}
function rgb(r, g, b){
  console.log(r,g,b)
  let result = decToHex(r)
    + decToHex(g) 
    + decToHex(b)
  console.log(result)
  return result
}
```