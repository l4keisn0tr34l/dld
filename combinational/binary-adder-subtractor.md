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

# parallel adder-subtractor

One circuit can add or subtract. A control input called mode `M` chooses the operation:

`Result = A + (B XOR M) + M`

- M=0: B unchanged and Cin=0 → `A+B`
- M=1: B inverted and Cin=1 → `A+B'+1 = A-B` (2's complement)

for signed 2's-complement addition, overflow is **carry into MSB XOR carry out of MSB**. carry-out alone is not signed overflow.

## rmr

- carry belongs to addition; borrow belongs to direct subtraction
- half circuit has no carry/borrow input
- XOR gives both half-adder sum and half-subtractor difference
