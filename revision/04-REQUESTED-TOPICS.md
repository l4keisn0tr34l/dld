# requested high-yield topics

# 1. BCD → Excess-3 and Excess-3 → BCD

## basic idea

- BCD stores every decimal digit in four bits.
- Excess-3 code = decimal digit +3, written in four-bit binary.
- Example: decimal 5 → BCD `0101`; add 3 → 8 → Excess-3 `1000`.

## full conversion table

| Decimal digit | BCD | Excess-3 |
|---:|---|---|
| 0 | `0000` | `0011` |
| 1 | `0001` | `0100` |
| 2 | `0010` | `0101` |
| 3 | `0011` | `0110` |
| 4 | `0100` | `0111` |
| 5 | `0101` | `1000` |
| 6 | `0110` | `1001` |
| 7 | `0111` | `1010` |
| 8 | `1000` | `1011` |
| 9 | `1001` | `1100` |

## BCD → Excess-3 circuit design

1. Write the table above.
2. BCD inputs `1010–1111` are invalid, so mark their outputs X.
3. Make one K-map for each of the four output bits.
4. Draw the simplified gate circuit.

For BCD input `A B C D` and Excess-3 output `W X Y Z`:

- `W=A+BC+BD`
- `X=B'C+B'D+BC'D'`
- `Y=CD+C'D'` — C XNOR D
- `Z=D'`

## Excess-3 → BCD circuit design

Reverse the same table. Valid Excess-3 inputs are only `0011–1100`; all unused words can be marked X.

For Excess-3 input `W X Y Z` and BCD output `A B C D`:

- `A=WX+WYZ`
- `B=XYZ+X'Y'+X'Z'`
- `C=YZ'+Y'Z` — Y XOR Z
- `D=Z'`

## common mistake

Do not convert the complete decimal number into ordinary binary. Convert **each decimal digit separately**.

Example: decimal 25:

- BCD=`0010 0101`
- Excess-3=`0101 1000`

# 2. encoder truth table

An encoder changes one active input line into a binary number.

## 8-to-3 encoder

Assume exactly one input is 1.

| active input | `Y2 Y1 Y0` |
|---|---|
| `D0` | `000` |
| `D1` | `001` |
| `D2` | `010` |
| `D3` | `011` |
| `D4` | `100` |
| `D5` | `101` |
| `D6` | `110` |
| `D7` | `111` |

Equations:

- `Y2=D4+D5+D6+D7`
- `Y1=D2+D3+D6+D7`
- `Y0=D1+D3+D5+D7`

A normal encoder becomes unclear when several inputs are 1. A priority encoder solves this by choosing the highest-priority input.

# 3. decoder truth table

A decoder changes a binary number into one active output line.

## 2-to-4 decoder

| A | B | Y0 | Y1 | Y2 | Y3 |
|---|---|---|---|---|---|
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 | 0 | 1 |

Equations:

- `Y0=A'B'`
- `Y1=A'B`
- `Y2=AB'`
- `Y3=AB`

Decoder outputs are minterms. Therefore, to implement `F=Σm(1,2,3)`, connect `Y1,Y2,Y3` to an OR gate.

## 3-to-8 decoder pattern

| ABC input | active output |
|---|---|
| `000` | Y0 |
| `001` | Y1 |
| `010` | Y2 |
| `011` | Y3 |
| `100` | Y4 |
| `101` | Y5 |
| `110` | Y6 |
| `111` | Y7 |

# 4. four-bit adder

A four-bit adder is simply **four full adders connected together**.

```text
A0,B0,C0 → FA0 → S0,C1
A1,B1,C1 → FA1 → S1,C2
A2,B2,C2 → FA2 → S2,C3
A3,B3,C3 → FA3 → S3,C4
```

- `A0,B0` are the rightmost/LSB bits.
- `C0` is the starting carry, normally 0.
- Each carry moves into the next full adder.
- `C4` is the final carry.

Each stage uses:

- `Si=Ai⊕Bi⊕Ci`
- `Ci+1=AiBi+AiCi+BiCi`

Example:

```text
  1011
+ 0110
------
1 0001
```

Four-bit output is `0001`; final carry is 1.

# 5. four-bit subtractor

## direct ripple-borrow method

Use four full subtractors:

```text
A0,B0,Bin0 → FS0 → D0,Borrow1
A1,B1,Borrow1 → FS1 → D1,Borrow2
A2,B2,Borrow2 → FS2 → D2,Borrow3
A3,B3,Borrow3 → FS3 → D3,Borrow4
```

Each stage uses:

- `Di=Ai⊕Bi⊕Bini`
- `Borrowout=Ai'Bi+Ai'Bini+BiBini`

## combined four-bit adder-subtractor

This version is more important. It uses four full adders and mode M:

`Result=A+(B XOR M)+M`

- `M=0`: B stays unchanged and starting carry is 0 → addition.
- `M=1`: every B bit is flipped and starting carry is 1 → subtraction.

Circuit drawing:

1. Draw four full adders.
2. Connect carry-out of each to carry-in of the next.
3. Put an XOR gate before every B input.
4. Connect M to every XOR and to the first carry-in.

Example: `0101−0011`:

- Flip B: `0011→1100`
- Add 1: `0101+1100+1=1 0010`
- Discard final carry → `0010`

# 6. BCD adder

## procedure

1. Add the two BCD digits like ordinary four-bit binary.
2. If there is a carry or result is greater than `1001` (9), add `0110`.
3. The correction carry goes to the next decimal digit.

Correction condition:

`K=C4+S3S2+S3S1`

## example: 8+7

```text
1000 + 0111 = 1111
1111 + 0110 = 1 0101
```

Result BCD=`0001 0101`=decimal 15.

## example: 27+35

- Ones: `7+5=12`; correct it → digit 2 and carry 1.
- Tens: `2+3+1=6`.
- Result=`0110 0010`=62.

## block diagram to draw

```text
A,B,Cin → [first 4-bit adder] → raw sum
                         │
                         └→ detector K

raw sum + (0110 when K=1) → [second 4-bit adder] → correct BCD digit
```

# 7. BCD subtractor

## 10's-complement method

To find `A−B`:

1. Take the 9's complement of every decimal digit of B.
2. Add 1 to make the 10's complement.
3. BCD-add this value to A.
4. If final carry appears, discard it. The answer is positive.
5. If no final carry appears, take the 10's complement of the result and attach a minus sign.

## positive example: 52−19

- 9's complement of 19=`80`.
- Add 1 → 10's complement=`81`.
- `52+81=133`.
- Discard final carry from the fixed two-digit answer → `33`.

## negative example: 35−72

- 9's complement of 72=`27`.
- Add 1 → 10's complement=`28`.
- `35+28=63`; no final carry.
- 10's complement of 63=`37`.
- Answer=`−37`.

## 9's-complement method

- Add A to the 9's complement of B.
- If an end carry appears, add that carry back to the rightmost digit.
- If no carry appears, take the 9's complement of the result and make it negative.

# final memory lines

- Encoder: one active line → binary number.
- Decoder: binary number → one active line.
- BCD→Excess-3: add 3 to every decimal digit.
- Four-bit adder: four full adders joined by carries.
- Four-bit subtractor: four full subtractors joined by borrows, or use the mode-controlled adder.
- BCD addition: invalid result → add 6.
- BCD subtraction: use 9's/10's complement.
