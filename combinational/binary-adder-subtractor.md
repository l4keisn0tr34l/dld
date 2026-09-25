# binary adders

An adder does normal addition on binary bits. A carry is the extra 1 passed to the next column, just like carrying in decimal addition.

## half adder

adds A and B only:

- sum `S=A⊕B`
- carry `C=AB`

## full adder

adds A, B and carry-in `Cin`:

- `S=A⊕B⊕Cin`
- `Cout=AB + Cin(A⊕B)`
- equivalent carry: `AB+ACin+BCin`

can be built using 2 half adders + OR. chaining full adders makes ripple-carry adder; carry delay ripples from LSB to MSB.

## 4-bit parallel adder

A 4-bit adder adds `A3A2A1A0` and `B3B2B1B0`. It uses **four full adders connected in a chain**:

1. FA0 adds `A0`, `B0` and input carry `C0`; it gives `S0` and `C1`.
2. FA1 adds `A1`, `B1` and `C1`; it gives `S1` and `C2`.
3. FA2 adds `A2`, `B2` and `C2`; it gives `S2` and `C3`.
4. FA3 adds `A3`, `B3` and `C3`; it gives `S3` and final carry `C4`.

The carry moves from the LSB full adder toward the MSB, so it is also called a **4-bit ripple-carry adder**.

Example: `1011+0110=1 0001`. The four-bit sum is `0001` and final carry is 1.

# binary subtractors

## half subtractor

computes `A-B`. A borrow is needed when a binary column tries to do `0-1`:

- difference `D=A⊕B`
- borrow `Bout=A'B`

## full subtractor

computes `A-B-Bin`:

- `D=A⊕B⊕Bin`
- `Bout=A'B + Bin(A⊕B)'`
- equivalent: `A'B + A'Bin + BBin`

## 4-bit parallel subtractor

A direct 4-bit subtractor uses **four full subtractors**:

- first stage calculates `A0−B0−Bin`
- its borrow-out enters the borrow-in of the next stage
- this continues up to the MSB

The result is `D3D2D1D0`, with a final borrow-out. This is called a ripple-borrow subtractor.

In practice, subtraction is more commonly done with full adders using the 2's complement of B.

# 4-bit parallel adder-subtractor

One 4-bit circuit can perform both operations using four full adders. Each B bit passes through an XOR gate with mode `M`, and the first carry-in is also M:

`Result = A + (B XOR M) + M`

- `M=0`: every `Bi XOR 0 = Bi` and `C0=0` → `A+B`
- `M=1`: every `Bi XOR 1 = Bi'` and `C0=1` → `A+B'+1=A−B`

For the diagram, draw four full adders in a row. Connect each carry-out to the next carry-in, put one XOR before every B input, and join all four XOR control inputs plus `C0` to M.

### one quick example

To calculate `0101−0011`, set M=1:

- invert B: `0011→1100`
- add the first carry 1: `0101+1100+1=1 0010`
- discard the final carry → answer `0010`

for signed 2's-complement addition, overflow is **carry into MSB XOR carry out of MSB**. carry-out alone is not signed overflow.

## rmr

- carry belongs to addition; borrow belongs to direct subtraction
- half circuit has no carry/borrow input
- XOR gives both half-adder sum and half-subtractor difference
