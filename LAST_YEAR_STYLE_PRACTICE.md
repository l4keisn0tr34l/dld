# practice based on last year's exam pattern

## what last year's paper tells us

The paper was **20 marks, 90 minutes, all compulsory**, with four questions of about 5 marks each. The examiner likes:

- small conversion/simplification questions
- one full tabulation problem
- asking for a circuit **using a particular device**, not only its normal gate circuit
- “design and explain operation” questions
- mixing two ideas, such as Gray code + odd detector or DEMUX/decoder + subtractor

Because your syllabus is larger this year, sequential-circuit questions may replace some old combinational questions.

# what to do in your final two hours

1. Attempt **Mock Paper A in 90 minutes** without notes.
2. Spend 20 minutes checking and correcting it.
3. Use the last 10 minutes on the starred backup questions at the bottom.

---

# mock paper A — most useful one

**Time: 1 hour 30 minutes**  
**Maximum marks: 20**  
**All questions are compulsory. Assume suitable missing data, if any.**

## Q1 — short fundamentals `[5 marks]`

### a. `[2 marks]`

Convert `(B7)₁₆` into:

1. ordinary binary
2. decimal
3. BCD
4. Gray code

Clearly show whether the Gray code is being formed from the binary representation of the number.

### b. `[1 mark]`

Simplify using Boolean algebra:

`Y = A'B(C+C'D) + B(A+A'C)`

### c. `[2 marks]`

Represent decimal `−13` in 8 bits using:

1. sign-magnitude
2. 1's complement
3. 2's complement

Also state the range of an 8-bit 2's-complement number.

## Q2 — minimization `[5 marks]`

### a. `[3 marks]`

Find the minimized SOP using the Quine–McCluskey/tabulation method:

`F(A,B,C,D)=Σm(0,1,2,5,6,7,8,9,10,14)+d(3,11)`

Show:

- groups according to number of 1s
- all combining rounds
- prime implicants
- prime-implicant chart
- final minimized expression

### b. `[1 mark]`

Find the dual of:

`Y=A'B+BC'(A+D)`

### c. `[1 mark]`

Write the canonical POS form of:

`F(A,B,C)=A+B'C`

Give the answer using both maxterm notation and expanded brackets.

## Q3 — combinational design `[5 marks]`

### a. `[3 marks]`

State the difference between a decoder and a DEMUX. Then implement a **full adder using a 3-to-8 decoder and OR gates**.

Your answer must contain:

- full-adder truth table
- minterm form of Sum and Carry
- decoder connections

### b. `[2 marks]`

Design a circuit that accepts a 4-bit binary number from 0 to 15 and gives output 1 only when the number is odd.

1. Write the required minterms.
2. Simplify the function.
3. Draw the final circuit.
4. Briefly state how the answer would change if the input were 4-bit Gray code instead of binary.

## Q4 — sequential design `[5 marks]`

### a. `[3 marks]`

Design a synchronous counter using JK flip-flops for the sequence:

`00 → 01 → 11 → 10 → 00`

Show:

- present-state/next-state table
- required J and K inputs
- simplified input equations
- final circuit

### b. `[2 marks]`

Compare a ring counter and Johnson counter. Write the complete state sequences of both for four flip-flops, starting from:

- ring counter: `1000`
- Johnson counter: `0000`

Also state the number of valid states produced by n flip-flops in each circuit.

---

# mock paper B — wider syllabus backup

Use this if u finish Paper A or want to replace topics u have not studied yet.

**Time: 1 hour 30 minutes**  
**Maximum marks: 20**

## Q1 `[5 marks]`

### a. `[2 marks]`

Using an 8-bit representation, perform `37−52` with the 2's-complement method. State whether the answer is positive or negative and verify its decimal value.

### b. `[2 marks]`

Minimize in POS using a K-map:

`F(A,B,C,D)=ΠM(0,2,5,7,8,10)+d(1,9)`

### c. `[1 mark]`

State De Morgan's theorems and use them to find the complement of `F=A(B+C')`.

## Q2 `[5 marks]`

### a. `[3 marks]`

Implement

`F(A,B,C)=Σm(1,2,6,7)`

using a 4:1 MUX with A and B as select lines. Find `I0,I1,I2,I3` in terms of C and draw the connections.

### b. `[2 marks]`

Design a 2-bit magnitude comparator for numbers `A1A0` and `B1B0`. Derive equations for:

- `A>B`
- `A=B`
- `A<B`

## Q3 `[5 marks]`

### a. `[3 marks]`

Design a one-decimal-digit BCD adder. Derive the correction condition and explain when and why `0110` is added. Use the circuit to add decimal 8 and 7.

### b. `[2 marks]`

Design a 4-bit parallel binary adder-subtractor using full adders and XOR gates. Explain the circuit for mode `M=0` and `M=1`.

## Q4 `[5 marks]`

### a. `[3 marks]`

Convert an available JK flip-flop so that it behaves as a D flip-flop. Show the conversion table, use the JK excitation table, simplify the equations and draw the final connections.

### b. `[2 marks]`

Explain SISO, SIPO, PISO and PIPO registers. Draw a 4-bit SIPO register and show its contents after serial bits `1,0,1,1` enter an initially cleared register. State your assumed shift direction.

---

# high-probability backup questions

Do the starred ones first if u have only a few minutes.

- [ ] ★ Implement a full subtractor using a 3-to-8 decoder and OR gates. Write `D=Σm(...)` and `Bout=Σm(...)` first.
- [ ] ★ Implement a full adder using two 4:1 MUXes, taking A and B as select lines.
- [ ] ★ Design and explain a one-digit BCD subtractor using the 10's-complement method.
- [ ] ★ Draw and explain a 4-bit binary subtractor using full adders, XOR gates and mode control.
- [ ] ★ Make the truth table and equations of a 4-to-2 priority encoder with `D3` as highest priority.
- [ ] Design a BCD-to-Excess-3 converter using four K-maps.
- [ ] Design a synchronous MOD-6 counter using D flip-flops, making unused states return to `000`.
- [ ] Convert D flip-flop to T flip-flop and T flip-flop to D flip-flop.
- [ ] Explain race-around in a JK flip-flop and methods used to remove it.
- [ ] Compare synchronous and asynchronous counters based on clocking, speed and propagation delay.

# checking points for mock paper A

Use these only after attempting it.

- Q1(a): `(B7)₁₆ = 10110111₂ = 183₁₀`; BCD must encode decimal digits `1`, `8`, `3` separately.
- Q1(c): begin with `+13 = 00001101`; do not complement the sign-magnitude answer.
- Q2(c): obtain the zero rows of `A+B'C`; canonical POS must contain every variable in every bracket.
- Q3(a): `Sum=Σm(1,2,4,7)` and `Carry=Σm(3,5,6,7)` for variable order `A,B,Cin`.
- Q3(b): for ordinary binary input, odd/even is decided by the LSB. For Gray input, first recover the binary LSB or derive it as XOR of the Gray bits.
- Q4(a): this sequence is a 2-bit Gray sequence; all flip-flops share the same clock.
- Q4(b): four FFs give 4 ring states and 8 Johnson states.
