# number systems

## what a number system/base means

The **base** tells us how many digits the system uses. Decimal has 10 digits; binary has only 2. A digit's value depends on both the digit and its position.

For base `r`, each position has value `r^position`.

`(1011.01)₂ = 1×2³ + 0×2² + 1×2¹ + 1×2⁰ + 0×2⁻¹ + 1×2⁻² = 11.25₁₀`

valid digits go from `0` to `r-1`:

- binary: 0,1
- octal: 0–7
- decimal: 0–9
- hex: 0–9,A–F (A=10 ... F=15)

## conversions

### any base → decimal

multiply every digit by its place weight and add. example above.

### decimal integer → another base

keep dividing by the new base. read remainders **bottom to top**.

`25₁₀ → binary`: remainders `1,0,0,1,1` → `11001₂`.

### decimal fraction → another base

keep multiplying fraction by new base. read integer parts **top to bottom**.

`0.625×2=1.25`, `.25×2=0.5`, `.5×2=1.0` → `.101₂`.

### binary ↔ octal / hex shortcut

- octal: groups of **3 bits**
- hex: groups of **4 bits**
- group outward from binary point; pad outer ends with zeroes

`11010110₂ = 326₈ = D6₁₆`.

# complements

## general rule in base r

- `(r-1)'s complement`: replace each digit `d` with `(r-1)-d`
- `r's complement`: `(r-1)'s complement + 1`

so:

| base | smaller complement | bigger complement |
|---|---|---|
| binary | 1's: flip every bit | 2's: flip + 1 |
| decimal | 9's: replace d by 9-d | 10's: 9's + 1 |

keep the **same number of digits**. This is called fixed width. For example, if the question says 5 bits, write `00101`, not `101`; their complements will be different.

## subtraction using r's complement

for `A-B` with n fixed digits:

1. take r's complement of B
2. add it to A
3. if carry comes out, discard carry → answer positive
4. no carry means answer negative; take r's complement of result to get magnitude

example: `1011-0110`: 2's comp of `0110`=`1010`; sum=`1 0101`; discard carry → `0101`.

## subtraction using (r-1)'s complement

same idea, but if carry appears **add that carry back to LSB** (end-around carry). no carry → complement result and mark negative.

# codes

## BCD (8421)

BCD means **Binary Coded Decimal**. Convert each decimal digit separately into 4-bit binary. `59₁₀ = 0101 1001 BCD`, **not** ordinary binary 59.

valid BCD nibbles: `0000` through `1001`; `1010`–`1111` invalid.

## excess-3

for each decimal digit: add 3, then encode in 4-bit binary.

`5 → 5+3=8 → 1000`. excess-3 is self-complementing: bitwise complement gives code for 9's-complement digit.

## gray code

adjacent values differ by only one bit.

binary → gray:

- MSB stays same
- every next gray bit = XOR of two neighboring binary bits
- formula: `G = B XOR (B >> 1)`

binary `1011` → gray `1110`.

gray → binary:

- MSB stays same
- each next binary bit = previous binary bit XOR current gray bit

## tiny things to rmr

- parity bit makes total number of 1s even (even parity) or odd (odd parity)
- BCD is weighted; gray and excess-3 are non-weighted
- excess-3 is self-complementing; ordinary 8421 BCD is not
