# Sum of positive [8 kyu]

You get an array of numbers, return the sum of all of the positives ones.

Example [1,-4,7,12]` => `1 + 7 + 12 = 20`

Note: if there is nothing to sum, the sum is default to 0.

## Solutions

```
#include <vector>

int positive_sum (const std::vector<int> arr){
  // Your code here
  int result = 0;
  for (int i=0; i<arr.size(); i++) {
    if (arr[i]>0) {
      result += arr[i];
    }
  }
  return result;
}
```