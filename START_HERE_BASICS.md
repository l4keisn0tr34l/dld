# start here if digital logic feels completely new

## the whole subject in one minute

Digital circuits work with only two values:

- `0` = LOW, false or OFF
- `1` = HIGH, true or ON

A **variable** like A or B is one binary value. A **bit** is one 0 or 1. Four bits are often called a **nibble**.

## symbols used in all notes

| symbol | meaning | example |
|---|---|---|
| `A'` | NOT A; reverse A | if A=1, A'=0 |
| `AB` or `A·B` | A AND B | 1 only when both are 1 |
| `A+B` | A OR B | 1 when either one is 1 |
| `A⊕B` | A XOR B | 1 when A and B are different |
| `A XNOR B` | opposite of XOR | 1 when A and B are equal |
| `Q` | value currently stored in a flip-flop | present state |
| `Q+` or `Q(next)` | value stored after next clock | next state |
| `X` | don't-care; may be treated as 0 or 1 | use whatever simplifies |

**Important:** in Boolean algebra, `+` means OR—not normal addition.

## common exam words

- **truth table:** table showing output for every possible input
- **complement:** opposite value; complement of 0 is 1 and vice versa
- **term:** one part of an expression, such as `AB'`
- **literal:** one appearance of a variable, such as A or A'
- **minimize:** write the same function using fewer gates/literals
- **MSB:** leftmost, highest-value bit
- **LSB:** rightmost, lowest-value bit
- **n-bit:** made of n binary digits; 4-bit means four 0s/1s
- **clock:** repeating signal telling storage circuits when to update
- **state:** values currently stored in a sequential circuit
- **active-high:** action happens at 1
- **active-low:** action happens at 0, often shown by a bubble or bar
- **propagation delay:** tiny time a real gate takes to produce its output

## two circuit families

### combinational circuit

Output depends only on inputs **right now**. Examples: adder, MUX and decoder.

### sequential circuit

Circuit remembers an old value. Output can depend on current inputs and stored value. Examples: flip-flops, registers and counters.

## how to use these notes

Read `README.md` in order. For each chapter:

1. learn the meaning and main rule
2. copy one worked example
3. close the note and solve two questions
4. check `WATCH_THESE.md` when the procedure needs a diagram

The notes still contain the formulas and terms expected in an exam. This file only gives you the language needed to understand them.
