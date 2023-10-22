# DNA to RNA Conversion [8 kyu]

Ribonucleic acid, RNA, is the primary messenger molecule in cells. RNA differs slightly from DNA its chemical structure and contains no Thymine. In RNA Thymine is replaced by another nucleic acid Uracil ('U').

Create a function which translates a given DNA string into RNA.

For example:

```
"GCAT"  =>  "GCAU"
```

The input string can be of arbitrary length - in particular, it may be empty. All input is guaranteed to be valid, i.e. each input string will only ever consist of `'G'`, `'C'`, `'A'` and/or `'T'`.

## Solution

```
#include <string>

std::string DNAtoRNA(std::string dna){
  std::string result;
  
  for (int i=0; i<dna.length(); i++) {
    if (dna[i]=='T') {
      result += 'U';
    }
    else {
      result += dna[i];
    }
  }
  
  return result;
}
```