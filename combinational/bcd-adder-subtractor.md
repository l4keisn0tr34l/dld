# BCD adder

BCD stores each decimal digit in its own group of 4 bits (a nibble). Add one 4-bit decimal digit at a time.

## correction rule

1. add two BCD digits + carry-in using binary adder
2. if result has carry OR 4-bit sum > `1001` (9), add `0110` (6)
3. correction generates decimal carry to next digit

why +6? Four bits have 16 possible patterns, but BCD uses only 10 (`0000` to `1001`). Adding 6 corrects an invalid binary result and produces the proper decimal carry.

correction signal for sum bits `S3 S2 S1 S0` and binary carry `C4`:

`K = C4 + S3S2 + S3S1 = C4 + S3(S2+S1)`

example: 8+7: binary sum `1111` (15), invalid. add `0110`: `1 0101` → BCD `0001 0101` = 15.

# BCD subtraction — 10's complement method

for fixed n decimal digits, `A-B`:

1. take 9's complement of every decimal digit of B
2. add 1 → 10's complement
3. BCD-add this to A, applying +6 correction per digit
4. final carry present: discard it, answer is positive
5. no final carry: take 10's complement of obtained result and attach minus sign

example with 2 digits: `52-19`.

- 9's comp of 19 = 80; +1 = 81
- `52+81=133`; discard end carry from fixed 2-digit result
- answer = 33

## subtraction using 9's complement

add A to 9's complement of B. if an end carry occurs, add it back to least-significant decimal digit (end-around carry). if not, 9's-complement result and mark negative.

## traps

- correction is per decimal digit, not once for whole word
- BCD `0001 0010` means decimal 12; straight binary value of those 8 bits isnt the point
- add 6 when carry occurs **even if displayed low nibble looks valid**
- preserve fixed number of decimal digits while taking complements
