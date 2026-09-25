# ride-to-uni revision — read this first

This is the whole syllabus in simple words. Do not try to learn a brand-new long method now; use this to wake up what u already studied.

# 1. number systems and codes

- Binary uses 0 and 1; octal uses 0–7; decimal uses 0–9; hex uses 0–9 and A–F.
- To convert any base to decimal, multiply each digit by its place value and add.
- Decimal integer to another base: repeatedly divide and read remainders from bottom upward.
- Decimal fraction to another base: repeatedly multiply and read whole-number parts from top downward.
- Binary↔octal: groups of 3 bits. Binary↔hex: groups of 4 bits.
- 1's complement: flip every bit. 2's complement: flip every bit and add 1.
- 9's complement: replace digit d with `9−d`. 10's complement: 9's complement +1.
- Complement subtraction: add the complement. If an end carry appears, discard it. Without carry, complement the result and mark it negative.
- BCD converts every decimal digit separately into four bits.
- Excess-3: add 3 to each decimal digit, then write four-bit binary.
- Binary→Gray: keep the first bit; XOR every neighboring binary pair.
- Gray→binary: keep the first bit; continue XOR from left to right.

# 2. Boolean algebra

- `+` means OR, letters together mean AND, and `'` means NOT.
- `A+0=A`, `A·1=A`, `A+1=1`, `A·0=0`.
- `A+A'=1`, `AA'=0`.
- `A+AB=A` and `A(A+B)=A`.
- De Morgan: remove NOT outside brackets by changing AND↔OR and complementing every variable.
- Dual: change AND↔OR and 0↔1, but do **not** complement variables.
- SOP is OR of AND terms and comes from output-1 rows.
- POS is AND of OR brackets and comes from output-0 rows.
- In a minterm, input 0 gives a complemented variable. In a maxterm, input 0 gives a normal variable.
- `Σm(...)` lists the 1 rows. `ΠM(...)` lists the 0 rows.

# 3. K-map

- Put columns/rows in Gray order: `00,01,11,10`.
- SOP: group 1s. POS: group 0s.
- Group sizes must be 1,2,4,8... Never 3 or 6.
- Make the biggest groups possible. Overlap is allowed.
- Left/right edges touch; top/bottom edges touch; four corners can form one group.
- A don't-care X may be used as 0 or 1 when it helps, but it never needs covering.
- In an SOP group: constant 1 stays normal; constant 0 gets complemented.
- In a POS group: constant 0 stays normal; constant 1 gets complemented.

# 4. tabulation method

1. Write minterms in binary.
2. Group them by number of 1s.
3. Combine two terms only if they differ in exactly one position; replace that position with `−`.
4. Repeat until nothing more combines.
5. Uncombined terms are possible final terms.
6. Make the chart, select terms that alone cover a required minterm, then cover leftovers cheaply.
7. Don't-cares help combining but do not need chart columns.
8. For POS, minimize `F'` using F's zero rows, then complement the answer with De Morgan.

# 5. MUX, DEMUX, encoder and decoder

- MUX = many inputs, one output. Select lines choose the input.
- DEMUX = one data input, many outputs. Select lines choose the output.
- Decoder = binary number in, one selected output line.
- Encoder = one selected input line, binary number out.
- Priority encoder chooses the highest input when several inputs are 1.
- A 4:1 MUX needs two select lines.
- To implement a function with a MUX, use some variables as selects. Remaining data inputs become `0,1,X,X'`.
- To implement `Σm(...)` with a decoder, OR the decoder outputs with those minterm numbers.
- Decoder vs DEMUX: decoder has code inputs; DEMUX additionally routes a data value D.

# 6. code converters

General method:

1. Make the input/output truth table.
2. Mark impossible inputs X if allowed.
3. Make one K-map for every output bit.
4. Draw gates from the simplified equations.

Binary→Gray:

- `G3=B3`
- `G2=B3⊕B2`
- `G1=B2⊕B1`
- `G0=B1⊕B0`

Gray→binary:

- `B3=G3`
- `B2=B3⊕G2`
- `B1=B2⊕G1`
- `B0=B1⊕G0`

In BCD-to-Excess-3, inputs 10–15 are impossible, so they can become X.

# 7. comparator and priority encoder

One-bit comparator:

- `A>B=AB'`
- `A<B=A'B`
- `A=B=A XNOR B`

For larger numbers, compare from the leftmost bit. Lower bits matter only while higher bits are equal.

For a 4-to-2 priority encoder with D3 highest:

- `Y1=D3+D2`
- `Y0=D3+D2'D1`
- `V=D3+D2+D1+D0`

V tells us whether any input is active.

# 8. binary adders and subtractors

Half adder:

- `S=A⊕B`
- `C=AB`

Full adder:

- `S=A⊕B⊕Cin`
- `Cout=AB+ACin+BCin`

Half subtractor:

- `D=A⊕B`
- `Borrow=A'B`

Full subtractor:

- `D=A⊕B⊕Bin`
- `Bout=A'B+A'Bin+BBin`

A four-bit adder is four full adders connected by carries. A four-bit direct subtractor is four full subtractors connected by borrows.

Combined four-bit circuit:

`Result=A+(B XOR M)+M`

- `M=0`: addition
- `M=1`: subtraction

# 9. BCD adder and subtractor

BCD addition:

1. Add the two four-bit digits normally.
2. If there is carry or the result is above 9, add `0110`.
3. Send decimal carry to the next digit.

Correction signal:

`K=C4+S3S2+S3S1`

BCD subtraction using 10's complement:

1. Take 9's complement of every digit of B.
2. Add 1.
3. BCD-add this to A.
4. End carry: discard it; answer is positive.
5. No end carry: take 10's complement of result and add a minus sign.

# 10. flip-flops

A flip-flop stores one bit. Q is the current stored bit; Q(next) is what it stores after the next clock.

- SR: 00 hold, 01 reset, 10 set, 11 invalid.
- JK: 00 hold, 01 reset, 10 set, 11 toggle.
- D: next Q equals D.
- T: T=0 holds; T=1 toggles.

Inputs needed for state changes:

| Q→next Q | SR | JK | D | T |
|---|---|---|---|---|
| 0→0 | 0X | 0X | 0 | 0 |
| 0→1 | 10 | 1X | 1 | 1 |
| 1→0 | 01 | X1 | 0 | 1 |
| 1→1 | X0 | X0 | 1 | 0 |

Race-around: a level-controlled JK with J=K=1 may toggle repeatedly while the clock stays active. Edge-triggered or master-slave construction avoids it.

# 11–14. survival facts for skipped topics

If u truly have no time, at least remember these one-line facts:

- Register = several flip-flops storing several bits.
- SISO/SIPO/PISO/PIPO describe serial or parallel input/output.
- Asynchronous counter: clock ripples from one flip-flop to the next; slower.
- Synchronous counter: all flip-flops receive the same clock; faster.
- MOD-N means N states. Needed FFs = smallest n where `2^n≥N`.
- Ring counter feeds last Q directly back; n FFs give n states.
- Johnson counter feeds last `Q'` back; n FFs give `2n` states.
- FF conversion means adding input logic so the available FF behaves like the wanted FF.
- JK→D: `J=D,K=D'`; JK→T: `J=K=T`; D→T: `D=T⊕Q`; T→D: `T=D⊕Q`.
