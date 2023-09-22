# Regex Password Validation [5 kyu]

[See Problem](https://www.codewars.com/kata/52e1476c8147a7547a000811)

You need to write regex that will validate a password to make sure it meets the following criteria:

- At least six characters long
- contains a lowercase letter
- contains an uppercase letter
- contains a digit
- only contains alphanumeric characters (note that '\_' is not alphanumeric)

## Solution

```
regex="^(?=.*?[A-Z])(?=.*?[a-z])(?=.*?[0-9])[A-Za-z0-9]{6,}$"
```