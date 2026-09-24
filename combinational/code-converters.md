# code converters

The same value can be written using different binary codes. A converter changes the representation without changing the actual value: input code → output code.

## universal design recipe

1. decide input/output bits
2. build conversion truth table
3. mark impossible/unused inputs as don't-cares (`X`), but only when the question allows them never to occur
4. make one K-map for **each output bit**
5. simplify, then draw circuit

## BCD → excess-3

valid BCD input is decimal 0–9. output is input digit + 3.

| decimal | BCD | excess-3 |
|---:|---|---|
| 0 | 0000 | 0011 |
| 1 | 0001 | 0100 |
| 2 | 0010 | 0101 |
| 3 | 0011 | 0110 |
| 4 | 0100 | 0111 |
| 5 | 0101 | 1000 |
| 6 | 0110 | 1001 |
| 7 | 0111 | 1010 |
| 8 | 1000 | 1011 |
| 9 | 1001 | 1100 |

BCD inputs 1010–1111 are invalid → X in all output maps.

## excess-3 → BCD

reverse table above. valid excess-3 words run from `0011` to `1100`; all unused input words are don't-cares.

## binary → gray

for binary `B3 B2 B1 B0`:

- `G3=B3`
- `G2=B3⊕B2`
- `G1=B2⊕B1`
- `G0=B1⊕B0`

## gray → binary

- `B3=G3`
- `B2=B3⊕G2`
- `B1=B2⊕G1`
- `B0=B1⊕G0`

or each B bit is cumulative XOR from MSB down.

## 4-bit binary → two-digit BCD

binary range is 0–15. outputs are tens nibble and ones nibble:

- 0–9: tens=`0000`, ones=same numerical value
- 10–15: tens=`0001`, ones=`0000` through `0101`

make truth table and simplify every output bit. dont confuse this with BCD input: binary `1111` is valid number 15.
