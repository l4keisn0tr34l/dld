# formula and table sheet

# Boolean identities

- `A+0=A`
- `A·1=A`
- `A+1=1`
- `A·0=0`
- `A+A=A`
- `AA=A`
- `A+A'=1`
- `AA'=0`
- `A+AB=A`
- `A(A+B)=A`
- `A+A'B=A+B`
- `A(A'+B)=AB`
- `(AB)'=A'+B'`
- `(A+B)'=A'B'`
- `(A+B)(A+C)=A+BC`
- `AB+AC=A(B+C)`

# minterm/maxterm rule

| input bit | minterm/SOP | maxterm/POS |
|---|---|---|
| 0 | complemented | normal |
| 1 | normal | complemented |

# code formulas

Binary→Gray:

`G3=B3, G2=B3⊕B2, G1=B2⊕B1, G0=B1⊕B0`

Gray→binary:

`B3=G3, B2=B3⊕G2, B1=B2⊕G1, B0=B1⊕G0`

# MUX/DEMUX

4:1 MUX:

`Y=I0S1'S0'+I1S1'S0+I2S1S0'+I3S1S0`

1:4 DEMUX:

- `Y0=DS1'S0'`
- `Y1=DS1'S0`
- `Y2=DS1S0'`
- `Y3=DS1S0`

# comparator

- `A>B=AB'`
- `A=B=A'B'+AB`
- `A<B=A'B`

# priority encoder

D3 highest:

- `Y1=D3+D2`
- `Y0=D3+D2'D1`
- `V=D3+D2+D1+D0`

# adders/subtractors

| circuit | first output | carry/borrow output |
|---|---|---|
| half adder | `S=A⊕B` | `C=AB` |
| full adder | `S=A⊕B⊕Cin` | `Cout=AB+ACin+BCin` |
| half subtractor | `D=A⊕B` | `Bout=A'B` |
| full subtractor | `D=A⊕B⊕Bin` | `Bout=A'B+A'Bin+BBin` |

Four-bit adder-subtractor:

`Result=A+(B XOR M)+M`

- `M=0`: add
- `M=1`: subtract

Signed overflow:

`overflow = carry into MSB XOR carry out of MSB`

# BCD correction

`K=C4+S3S2+S3S1`

If K=1, add `0110`.

# flip-flop characteristic table

| FF | inputs | action |
|---|---|---|
| SR | 00 | hold |
| SR | 01 | reset to 0 |
| SR | 10 | set to 1 |
| SR | 11 | invalid |
| JK | 00 | hold |
| JK | 01 | reset to 0 |
| JK | 10 | set to 1 |
| JK | 11 | toggle |
| D | D | next Q=D |
| T | 0 | hold |
| T | 1 | toggle |

Characteristic equations:

- SR: `Q(next)=S+R'Q`
- JK: `Q(next)=JQ'+K'Q`
- D: `Q(next)=D`
- T: `Q(next)=T⊕Q`

# excitation table

| change wanted | SR | JK | D | T |
|---|---|---|---|---|
| 0→0 | 0X | 0X | 0 | 0 |
| 0→1 | 10 | 1X | 1 | 1 |
| 1→0 | 01 | X1 | 0 | 1 |
| 1→1 | X0 | X0 | 1 | 0 |

# direct FF conversions

- JK→D: `J=D`, `K=D'`
- JK→T: `J=T`, `K=T`
- D→JK: `D=JQ'+K'Q`
- D→T: `D=T⊕Q`
- T→D: `T=D⊕Q`
- SR→D: `S=D`, `R=D'`

# skipped-topic formulas

- Counter FF count: smallest n where `2^n≥N`
- Ring states with n FFs: n
- Johnson states with n FFs: `2n`
- Synchronous up-counter T inputs: `T0=1`, `T1=Q0`, `T2=Q1Q0`
