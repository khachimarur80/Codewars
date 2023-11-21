# Validate Sudoku with size `NxN` [4 kyu]

Given a Sudoku data structure with size `NxN, N > 0 and √N == integer`, write a method to validate if it has been filled out correctly.

The data structure is a multi-dimensional Array, i.e:
```
[
  [7,8,4,  1,5,9,  3,2,6],
  [5,3,9,  6,7,2,  8,4,1],
  [6,1,2,  4,3,8,  7,5,9],
  
  [9,2,8,  7,1,5,  4,6,3],
  [3,5,7,  8,4,6,  1,9,2],
  [4,6,1,  9,2,3,  5,8,7],
  
  [8,7,6,  3,9,4,  2,1,5],
  [2,4,3,  5,6,1,  9,7,8],
  [1,9,5,  2,8,7,  6,3,4]
]
```

Rules for validation

- Data structure dimension: `NxN` where `N > 0` and `√N == integer`
- Rows may only contain integers: `1..N (N included)`
- Columns may only contain integers: `1..N (N included)`
- 'Little squares' (`3x3` in example above) may also only contain integers: `1..N (N included)`

## Solution

```
var Sudoku = function(data) 
{
  const N = data.length
  
  let sudokuForm = N == Math.max(...data.map(row => row.length))
  let validRows = true
  let validCols = true
  let validSquares = true
  let isSingle = (N==1 && data[0][0]===1) || (N!=1)
  
  let cols = []
  
  for (let i=0; i<N; i++) {
    let items = new Set(data[i])
    validRows = items.size == N
    
    if (i==0) {
      cols = data[i].map(item => [item])
    }
    else {
      for (let j=0; j<N; j++) {
        validCols = !cols[j].includes(data[i][j])
        cols[j].push(data[i][j])
      }
    }
  }
  
  let squareSize = parseInt(N**.5)
  
  for (let i=0; i<squareSize; i++) {
    for (let j=0; j<squareSize; j++) {
      let squareRows = data.slice(i*squareSize, (i+1)*squareSize)
      let square = squareRows.map(row => row.slice(j*squareSize, (j+1)*squareSize))
      
      square = square.flat().map(Number)
      let uniques = new Set(square)
      
      validSquares = uniques.size == N
    }
  }
  
  return {
    isValid: function() {
      // YOUR SOLUTION
      if (N==1) {
        console.log(data)
      }
      return isSingle && sudokuForm && validCols && validRows && validSquares;
    }
  };
};
```