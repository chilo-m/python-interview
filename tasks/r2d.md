Римские цифры
```
/*
input: correct Roman number from the interval [1,3999]
output: int representation of the number
XXV = 25
*/

var R2I = map[rune]int{
    'I': 1,
    'V': 5,
    'X': 10,
    'L': 50,
    'C': 100,
    'D': 500,
    'M': 1000,
}

R2I = {
    'I': 1,
    'V': 5,
    'X': 10,
    'L': 50,
    'C': 100,
    'D': 500,
    'M': 1000
}

func main() {
    for _, r := range []struct {
        Roman    string
        Expected int
    }{
        {"I", 1}, {"II", 2}, {"III", 3}, {"IV", 4}, {"V", 5}, {"VI", 6}, {"VII", 7}, {"VIII", 8}, {"IX", 9}, {"X", 10},
        {"MCMLXXXIV", 1984}, {"MCMXCIX", 1999}, {"MMXXI", 2021},
    } {
        actual := R2D(r.Roman)
        if actual == r.Expected {
            fmt.Printf("%s: OK\n", r.Roman)
        } else {
            fmt.Printf("%s: got %d, but expect %d\n", r.Roman, actual, r.Expected)
        }
    }
}
```
Решение python
```python
def R2D(roman: str) -> int:
    result = 0
    prev_digit = 0
    for letter in roman:
        digit = R2I[letter]
        if prev_digit < digit:
            result -= prev_digit * 2
        result += digit
        prev_digit = digit
    return result
```
Решение Go
```go
package main
 
import (
    "fmt"
)
func R2D(roman string) int {
    result := 0
    prev_digit := 0
    for _, letter := range roman {
        digit := R2I[letter]
        if prev_digit < digit {
            result -= prev_digit + prev_digit
        }
        result += digit
        prev_digit = digit
    }
    return result
}
```