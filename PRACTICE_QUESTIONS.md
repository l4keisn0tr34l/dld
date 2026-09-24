# questions u should practice

Do these with pen and paper. A question counts as complete only if u can do it **without opening the notes**.

- `★` = minimum practice; do these first
- `◆` = harder exam-style question
- For circuit questions, write the truth/state table, simplify the equations, and draw the circuit.

# 1. number systems, codes and complements

- [ ] ★ Convert `(101101.011)₂` to decimal.
- [ ] ★ Convert `(347)₈` to binary and hexadecimal.
- [ ] ★ Convert `(156.625)₁₀` to binary.
- [ ] Find the 1's and 2's complements of `00101101`.
- [ ] Find the 9's and 10's complements of decimal `2746`, keeping four digits.
- [ ] ★ Use 2's complement to calculate `10110₂ - 01101₂`.
- [ ] ◆ Use 2's complement to calculate `01001₂ - 10111₂`; show how u identify a negative answer.
- [ ] Write decimal 59 in ordinary binary, BCD and Excess-3. Explain why the three answers differ.
- [ ] Convert binary `101101` to Gray code, then convert your Gray answer back to binary.

# 2. Boolean algebra

Simplify using laws and name the important law used:

- [ ] ★ `A + AB`
- [ ] ★ `AB + AB'`
- [ ] `A + A'B`
- [ ] `(A+B)(A+B')`
- [ ] `AB + A'C + BC`
- [ ] ★ Find the complement of `F=A(B+C')` using De Morgan's law.
- [ ] Write the dual of `A+BC=(A+B)(A+C)`.
- [ ] From truth-table rows where `F=1` at indices `1,2,5,7`, write canonical SOP.
- [ ] For the same function, write canonical POS.
- [ ] Convert `F=A+B'C` into canonical SOP for variables A, B and C.

# 3. K-map minimization

For every question, draw a correctly labelled Gray-code K-map and give the simplified expression.

- [ ] ★ SOP: `F(A,B,C)=Σm(1,2,3,5,7)`.
- [ ] ★ SOP: `F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)`.
- [ ] ★ POS: `F(A,B,C)=ΠM(0,2,6,7)`.
- [ ] SOP with don't-cares: `F=Σm(1,3,7,11,15)+d(0,2,5)`.
- [ ] POS with don't-cares: `F=ΠM(0,1,5,7,8,9,13,15)+d(2,3)`.
- [ ] ◆ Make one example containing a corner group, an overlapping group and a don't-care. Explain why every group is legal.

# 4. tabulation / Quine–McCluskey

Show grouping by number of 1s, every combining round, prime implicants, and the PI chart.

- [ ] ★ Minimize `F(A,B,C,D)=Σm(0,1,2,5,6,7,8,9,10,14)`.
- [ ] Minimize `F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)` using tabulation, not a K-map.
- [ ] Minimize `F=Σm(1,3,7,11,15)+d(0,2,5)`.
- [ ] ★ Obtain minimal POS for `F=ΠM(0,2,5,7,8,10)` by tabulating `F'`.
- [ ] Explain why don't-care terms may help create prime implicants but do not get columns in the PI chart.

# 5. encoder, decoder, MUX and DEMUX

- [ ] ★ Draw a 2-to-4 decoder truth table and derive all four output equations.
- [ ] Implement `F(A,B,C)=Σm(1,2,6,7)` using a 3-to-8 decoder and one OR gate.
- [ ] Draw an 8-to-3 encoder truth table, assuming exactly one input is active.
- [ ] ★ Write the output equation of a 4:1 MUX.
- [ ] Implement `F(A,B,C)=Σm(1,2,6,7)` using a 4:1 MUX with A and B as select lines. Find `I0,I1,I2,I3` in terms of C.
- [ ] Draw a 1:4 DEMUX and derive its output equations.
- [ ] Give one real application each of an encoder, decoder, MUX and DEMUX.
- [ ] Explain the difference between a decoder and DEMUX in two sentences.

# 6. code converters

- [ ] ★ Make the complete truth table for BCD-to-Excess-3 conversion, including invalid BCD inputs as don't-cares.
- [ ] Use four K-maps to derive all output equations for that converter.
- [ ] Design an Excess-3-to-BCD converter using the same full process.
- [ ] ★ Derive equations for a 4-bit binary-to-Gray converter.
- [ ] Derive equations for a 4-bit Gray-to-binary converter.
- [ ] ◆ Make the truth table for a 4-bit binary-to-two-digit-BCD converter for inputs 0 through 15. State how many output bits are required.

# 7. magnitude comparator and priority encoder

- [ ] ★ Derive `A>B`, `A=B` and `A<B` for a 1-bit comparator.
- [ ] Derive all three equations for a 2-bit comparator.
- [ ] Compare `A=1011` and `B=1001` by checking bits from MSB to LSB. State where the answer becomes certain.
- [ ] ★ Make a truth table for a 4-to-2 priority encoder where `D3` has highest priority.
- [ ] Derive its two output equations and valid-bit equation.
- [ ] Explain why the valid bit is needed when the encoded output is `00`.

# 8. binary adders and subtractors

- [ ] ★ Derive sum and carry equations of a half adder from its truth table.
- [ ] ★ Make the full-adder truth table and derive `S` and `Cout`.
- [ ] Show how two half adders and an OR gate make a full adder.
- [ ] Derive difference and borrow equations of a half subtractor.
- [ ] ★ Make the full-subtractor truth table and derive `D` and `Bout`.
- [ ] Calculate `1011+0110` using a 4-bit ripple-carry process; show every carry.
- [ ] Explain and draw a 4-bit parallel adder-subtractor using XOR gates and mode M.
- [ ] ◆ Add `0111+0011` as 4-bit signed 2's-complement values. Identify overflow using carry into/out of the MSB.

# 9. BCD adder and subtractor

- [ ] ★ Perform BCD addition: `27+35`; show binary addition and every `+0110` correction.
- [ ] ★ Perform BCD addition: `58+76`.
- [ ] Derive the correction condition `K=C4+S3S2+S3S1`.
- [ ] Explain in simple words why 6 is added after an invalid BCD result.
- [ ] ★ Use the 10's-complement method to calculate `52-19` in BCD.
- [ ] Use the 10's-complement method to calculate `35-72`; show how the negative result is found.
- [ ] ◆ Draw the block diagram of a one-digit BCD adder, including correction detection and the second adder.

# 10. flip-flops

- [ ] ★ From memory, write characteristic tables for SR, JK, D and T flip-flops.
- [ ] ★ From memory, write the combined excitation table for all four flip-flops.
- [ ] Derive characteristic equations for SR, JK, D and T.
- [ ] For each JK input/state combination, calculate `Q(next)` when Q=0 and when Q=1.
- [ ] Given D inputs `1,0,1,1,0` over five clock edges and initial Q=0, draw Q.
- [ ] Explain race-around in a level-triggered JK flip-flop and give two ways to avoid it.
- [ ] Explain the difference between synchronous input and asynchronous preset/clear.

# 11. registers

- [ ] ★ Explain SISO, SIPO, PISO and PIPO without looking at the table.
- [ ] Draw a 4-bit SIPO register using D flip-flops.
- [ ] Starting from `0000`, shift serial bits `1,0,1,1` through it and write the state after every clock. Clearly state your shift direction.
- [ ] Draw a 4-bit PISO register and explain load mode versus shift mode.
- [ ] State the four operations of a universal shift register.
- [ ] Explain why a 4-bit register needs four flip-flops.

# 12. synchronous and asynchronous counters

- [ ] ★ Draw a 3-bit asynchronous up counter and write its eight-state sequence.
- [ ] Explain why it is called a ripple counter and why temporary false states can appear.
- [ ] Find the number of flip-flops needed for MOD-6, MOD-10 and MOD-16 counters.
- [ ] ★ Derive T-input equations for a 3-bit synchronous binary up counter.
- [ ] Derive T-input equations for a 3-bit synchronous binary down counter.
- [ ] Design a synchronous counter with sequence `000→001→011→010→000` using JK flip-flops.
- [ ] ◆ Design a synchronous MOD-6 counter using D flip-flops. Decide what unused states 110 and 111 should do so it is self-starting.
- [ ] Draw a MOD-10 ripple counter and show which state must be decoded to reset it.

# 13. ring and Johnson counters

- [ ] ★ Write the full state sequence of a 4-bit ring counter starting at `1000`.
- [ ] Explain why an all-zero ring counter gets stuck.
- [ ] ★ Write the full state sequence of a 4-bit Johnson counter starting at `0000`.
- [ ] How many valid states do 5-bit ring and 5-bit Johnson counters have?
- [ ] Draw both counters using D flip-flops and clearly show the difference in feedback.
- [ ] Given an unfamiliar shift direction, calculate the next four states without updating flip-flops one at a time.

# 14. conversion of flip-flops

For each conversion, show the conversion table, use the available FF's excitation table, simplify with a K-map, and draw the final connection.

- [ ] ★ Convert available JK flip-flop into D flip-flop.
- [ ] ★ Convert available JK flip-flop into T flip-flop.
- [ ] Convert available D flip-flop into JK flip-flop.
- [ ] Convert available D flip-flop into T flip-flop.
- [ ] Convert available T flip-flop into D flip-flop.
- [ ] Convert available SR flip-flop into D flip-flop.
- [ ] ◆ Convert available JK flip-flop into SR behavior, handling the invalid desired SR input correctly.
- [ ] Explain the difference between “convert JK to D” and “convert D to JK.”

# final mock-paper checklist

After finishing chapter-wise practice, attempt this in one sitting without notes:

1. one number conversion + one complement subtraction
2. one Boolean simplification
3. one 4-variable K-map with don't-cares
4. one tabulation question
5. one MUX/decoder implementation
6. one code-converter design
7. one comparator or priority encoder
8. one binary adder/subtractor
9. one BCD addition/subtraction
10. one flip-flop table question
11. one register timing/state question
12. one synchronous counter design
13. one ring/Johnson sequence
14. one flip-flop conversion

Mark every mistake by type: **concept**, **formula**, **careless calculation**, or **ran out of time**. Revise the type that repeats most.

# about part b

u forgot what part **b** was—that's fine. tell me whenever u remember and it can be added here or made into its own file.
