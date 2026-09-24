# magnitude comparator

A magnitude comparator checks which binary number is larger. It gives three outputs: `A>B`, `A=B`, `A<B`. Only one output should be 1 at a time.

## 1-bit comparator

- `A>B = AB'`
- `A<B = A'B`
- `A=B = A XNOR B = A'B'+AB`

## multi-bit idea

compare from **MSB first**. lower bits matter only if every higher pair is equal.

for 2 bits `A1A0` and `B1B0`, let `E1=A1 XNOR B1`:

- `A>B = A1B1' + E1·A0B0'`
- `A<B = A1'B1 + E1·A0'B0`
- `A=B = E1(A0 XNOR B0)`

comparators can be cascaded for larger words.

# priority encoder

A normal encoder expects only one input to be 1. If several are 1, its answer becomes unclear. A priority encoder solves this by ignoring lower-priority inputs and encoding the highest-priority 1.

## 4-to-2, D3 highest priority

| inputs condition | Y1Y0 | valid V |
|---|---|---|
| `D3=1` | 11 | 1 |
| `D3=0,D2=1` | 10 | 1 |
| `D3=D2=0,D1=1` | 01 | 1 |
| only `D0=1` | 00 | 1 |
| all zero | 00 | 0 |

`V` distinguishes D0 from no active input.

for this active-high version:

- `Y1 = D3 + D2`
- `Y0 = D3 + D2'D1`
- `V = D3+D2+D1+D0`

priority order must be stated; some chips are active-low, so always inspect bubbles/truth table.
