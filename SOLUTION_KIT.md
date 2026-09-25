# solution kit

Use this **after attempting or mentally planning a question**. For circuit-design questions, the answer below gives the equations and required structure; draw standard gate/FF symbols yourself.

# solutions to `PRACTICE_QUESTIONS.md`

## 1. number systems, codes and complements

1. `(101101.011)₂ = 32+8+4+1+0.25+0.125 = 45.375₁₀`.
2. `(347)₈ = 011 100 111₂ = 11100111₂ = E7₁₆`.
3. `156₁₀=10011100₂`; `.625=.101₂`; answer `10011100.101₂`.
4. For `00101101`: 1's complement=`11010010`; 2's complement=`11010011`.
5. For decimal `2746`: 9's complement=`7253`; 10's complement=`7254`.
6. `10110−01101`: 2's comp of `01101`=`10011`; sum=`1 01001`; discard carry → `01001`.
7. `01001−10111`: 2's comp of `10111`=`01001`; sum=`10010`, no carry. Complement `10010` to get magnitude `01110`; answer `−14`.
8. Decimal 59: ordinary binary=`111011`; BCD=`0101 1001`; Excess-3=`1000 1100`. BCD/Excess-3 encode each decimal digit separately.
9. `101101₂ → 111011 Gray`. Converting `111011` back gives `101101`.

## 2. Boolean algebra

1. `A+AB=A` — absorption.
2. `AB+AB'=A(B+B')=A`.
3. `A+A'B=A+B`.
4. `(A+B)(A+B')=A`.
5. `AB+A'C+BC=AB+A'C`; `BC` is the consensus/redundant term.
6. If `F=A(B+C')`, then `F'=A'+(B+C')'=A'+B'C`.
7. Dual of `A+BC=(A+B)(A+C)` is `A(B+C)=AB+AC`.
8. `F=Σm(1,2,5,7)=A'B'C+A'BC'+AB'C+ABC`.
9. Remaining zero indices are `0,3,4,6`, so `F=ΠM(0,3,4,6)`.
10. `A+B'C=Σm(1,4,5,6,7)`.

## 3. K-map

1. `Σm(1,2,3,5,7) → F=C+A'B`.
2. `Σm(0,2,5,7,8,10,13,15) → F=B'D'+BD` (B XNOR D).
3. `ΠM(0,2,6,7) → F=(A+C)(A'+B')`.
4. `Σm(1,3,7,11,15)+d(0,2,5) → F=CD+A'B'`.
5. `ΠM(0,1,5,7,8,9,13,15)+d(2,3) → F=(B+C)(B'+D')`.
6. Any valid answer must use power-of-two rectangular groups. A corner group contains the four corners because opposite edges touch; overlap is allowed when it reduces literals.

## 4. tabulation

1. `Σm(0,1,2,5,6,7,8,9,10,14) → F=CD'+B'C'+A'BD`.
2. `Σm(0,2,5,7,8,10,13,15) → F=B'D'+BD`.
3. `Σm(1,3,7,11,15)+d(0,2,5) → F=CD+A'B'`.
4. For zeros `0,2,5,7,8,10`, minimize `F'`; final `F=(B+D)(A+B'+D')`.
5. Don't-cares may be used to form larger groups, but they are not required output values, so they receive no PI-chart columns.

## 5. encoder, decoder, MUX and DEMUX

1. 2-to-4 decoder: `Y0=A'B'`, `Y1=A'B`, `Y2=AB'`, `Y3=AB`.
2. For `Σm(1,2,6,7)`, connect decoder outputs `Y1,Y2,Y6,Y7` to an OR gate.
3. 8-to-3 encoder: active `D0...D7` produces `000...111`. Equations: `Y2=D4+D5+D6+D7`, `Y1=D2+D3+D6+D7`, `Y0=D1+D3+D5+D7` under one-active-input assumption.
4. 4:1 MUX: `Y=I0S1'S0'+I1S1'S0+I2S1S0'+I3S1S0`.
5. For `F=Σm(1,2,6,7)` with selects AB: `I0=C`, `I1=C'`, `I2=0`, `I3=1`.
6. 1:4 DEMUX: `Y0=DS1'S0'`, `Y1=DS1'S0`, `Y2=DS1S0'`, `Y3=DS1S0`.
7. Applications: encoder—keyboard code; decoder—memory selection; MUX—select one data source; DEMUX—route one source to destinations.
8. Decoder converts an n-bit code into one selected output. DEMUX routes an actual data input D to one selected output.

## 6. code converters

Let BCD inputs be `A B C D` and Excess-3 outputs `W X Y Z`.

1–2. BCD→Excess-3 table is decimal `0...9` mapped to binary `3...12`; inputs `10...15` are X. Minimized equations:

- `W=A+BC+BD`
- `X=B'C+B'D+BC'D'`
- `Y=CD+C'D'`
- `Z=D'`

3. Excess-3→BCD, for valid inputs 3...12:

- `A=WX+WYZ`
- `B=XYZ+X'Y'+X'Z'`
- `C=YZ'+Y'Z`
- `D=Z'`

4. Binary→Gray: `G3=B3`, `G2=B3⊕B2`, `G1=B2⊕B1`, `G0=B1⊕B0`.
5. Gray→binary: `B3=G3`, `B2=G3⊕G2`, `B1=G3⊕G2⊕G1`, `B0=G3⊕G2⊕G1⊕G0`.
6. Binary→BCD needs 8 outputs: four tens bits and four ones bits. For 0–15, only tens LSB can be 1: `T0=AB+AC`. Ones equations: `O3=AB'C'`, `O2=BC+ A'B`, `O1=A'C+ABC'`, `O0=D`; all other tens bits are 0.

## 7. comparator and priority encoder

1. One-bit: `A>B=AB'`, `A=B=A XNOR B`, `A<B=A'B`.
2. Let `E1=A1 XNOR B1`, `E0=A0 XNOR B0`: `A>B=A1B1'+E1A0B0'`; `A<B=A1'B1+E1A0'B0`; `A=B=E1E0`.
3. `1011>1001`; the MSBs first differ at the second-from-right comparison `1>0` after equal higher bits.
4–5. With `D3` highest: `Y1=D3+D2`, `Y0=D3+D2'D1`, `V=D3+D2+D1+D0`.
6. Output `00` can mean D0 is active or nothing is active; V separates those cases.

## 8. binary adders and subtractors

1. Half adder: `S=A⊕B`, `C=AB`.
2. Full adder: `S=A⊕B⊕Cin`; `Cout=AB+ACin+BCin`.
3. First HA adds A,B; second adds first sum,Cin; OR both carries.
4. Half subtractor: `D=A⊕B`, `Bout=A'B`.
5. Full subtractor: `D=A⊕B⊕Bin`; `Bout=A'B+A'Bin+BBin`.
6. `1011+0110=10001`. From LSB, carries are 0,1,1,1 into successive columns and final carry 1.
7. Use four full adders. Feed each B through XOR with M and set first `Cin=M`: M=0 gives addition; M=1 gives `A+B'+1=A−B`.
8. `0111+0011=1010`; two positive signed values produced a negative-looking result. Carry into MSB=1, carry out=0, so overflow=1.

## 9. BCD adder and subtractor

1. `27+35`: units `7+5=1100`, add `0110` → carry 1 and `0010`; tens `2+3+1=6`; result BCD `0110 0010` = 62.
2. `58+76`: units gives 4 carry 1; tens `5+7+1=13`, correct to decimal carry 1 and digit 3; result `0001 0011 0100` = 134.
3. Invalid when `C4=1` or sum is 10–15. For 10–15, `S3=1` and either `S2` or `S1` is 1: `K=C4+S3S2+S3S1`.
4. Adding 6 skips the six invalid 4-bit patterns between decimal digits 9 and the next decimal carry.
5. `52−19`: 10's complement of 19 is 81; `52+81=133`; discard final carry → 33.
6. `35−72`: 10's complement of 72 is 28; `35+28=63`, no end carry; 10's complement of 63 is 37 → `−37`.
7. Block diagram: first 4-bit adder → correction detector K → second adder adds `0110` when K=1 → decimal carry.

## 10. flip-flops

1. Characteristic tables are in `sequential/flip-flops.md`: SR 00 hold/01 reset/10 set/11 invalid; JK 00 hold/01 reset/10 set/11 toggle; D next=D; T 0 hold/1 toggle.
2. Excitation table: `0→0: SR=0X, JK=0X,D=0,T=0`; `0→1:10,1X,1,1`; `1→0:01,X1,0,1`; `1→1:X0,X0,1,0`.
3. `SR: Q+=S+R'Q`; `JK: Q+=JQ'+K'Q`; `D:Q+=D`; `T:Q+=T⊕Q`.
4. Apply `Q+=JQ'+K'Q`; JK 00 holds, 01 resets, 10 sets, 11 toggles.
5. D sequence from Q=0 after edges: `1,0,1,1,0`.
6. Race-around: level-triggered JK with J=K=1 toggles repeatedly during a long active clock. Use edge-triggered/master-slave FF or shorter pulse.
7. Synchronous input acts at the clock event; asynchronous preset/clear acts immediately.

## 11. registers

1. SISO serial/serial; SIPO serial/parallel; PISO parallel/serial; PIPO parallel/parallel.
2. Four D FFs share a clock; each Q feeds the next D; first D is serial input.
3. Assuming new bit enters left and old bits shift right: `0000→1000→0100→1010→1101` for inputs 1,0,1,1. Reverse convention gives reversed placement but is valid if stated.
4. PISO uses selection logic: load mode places four parallel bits into FFs; shift mode passes each Q toward serial output.
5. Universal register: hold, shift left, shift right, parallel load.
6. One FF stores one bit, so four bits require four FFs.

## 12. counters

1. Three-bit ripple sequence: `000,001,010,011,100,101,110,111,000`.
2. Each FF clocks the next, so changes ripple and propagation delays briefly create false intermediate outputs.
3. MOD-6→3 FFs; MOD-10→4; MOD-16→4.
4. Three-bit synchronous up with T FFs: `T0=1`, `T1=Q0`, `T2=Q1Q0`.
5. Down counter: `T0=1`, `T1=Q0'`, `T2=Q1'Q0'`.
6. For `000→001→011→010→000`, Q2 remains 0. For Q1Q0: `J1=Q0`, `K1=Q0'`, `J0=Q1'`, `K0=Q1`. Force/recover Q2 appropriately.
7. MOD-6 D design state table: `000→001→010→011→100→101→000`, and `110,111→000`. Equations: `D2=Q2'Q1Q0+Q2Q1'Q0'`; `D1=Q2'Q1'Q0+Q2'Q1Q0'`; `D0=Q0'(Q1'+Q2')`.
8. MOD-10 ripple uses four FFs and decodes `1010`; decoded signal clears to `0000`.

## 13. ring and Johnson counters

1. Ring: `1000→0100→0010→0001→1000`.
2. Direct feedback of zero keeps loading zero, so `0000` never escapes.
3. Johnson: `0000→1000→1100→1110→1111→0111→0011→0001→0000`.
4. Five-bit ring=5 states; five-bit Johnson=10 states.
5. Both are shift registers; ring feeds last Q directly to first D, Johnson feeds last `Q'`.
6. Calculate all next bits from the old state simultaneously; never use an already-updated bit.

## 14. flip-flop conversion

1. JK→D: `J=D`, `K=D'`.
2. JK→T: `J=T`, `K=T`.
3. D→JK: `D=JQ'+K'Q`.
4. D→T: `D=T⊕Q`.
5. T→D: `T=D⊕Q`.
6. SR→D: `S=D`, `R=D'`.
7. JK→SR behavior: for valid SR inputs, use desired `Q+=S+R'Q`, then JK excitation table/K-maps. One safe realization is `J=S`, `K=R`; exclude desired S=R=1.
8. “JK to D” means JK hardware is available and D behavior is wanted; “D to JK” means the opposite.

# solutions to `LAST_YEAR_STYLE_PRACTICE.md`

## Mock Paper A

### Q1

**(a)** `(B7)₁₆=10110111₂=183₁₀`. BCD=`0001 1000 0011`. Gray from `10110111` is `11101100`.

**(b)** `Y=A'B(C+C'D)+B(A+A'C)=A'B(C+D)+B(A+C)=B(A+C+D)`.

**(c)** `+13=00001101`. Sign-magnitude `−13=10001101`; 1's complement=`11110010`; 2's complement=`11110011`. Eight-bit 2's-complement range is `−128...+127`.

### Q2

**(a)** `F=Σm(0,1,2,5,6,7,8,9,10,14)+d(3,11)` minimizes to `F=B'+CD'+A'D`.

**(b)** Dual of `A'B+BC'(A+D)` is `(A'+B)(B+C'+AD)`.

**(c)** `A+B'C` is zero at 0,2,3. `F=ΠM(0,2,3)=(A+B+C)(A+B'+C)(A+B'+C')`.

### Q3

**(a)** Decoder has code inputs; DEMUX also has data D. Full adder with variable order A,B,Cin: `Sum=Σm(1,2,4,7)` and `Carry=Σm(3,5,6,7)`. OR those decoder outputs separately.

**(b)** Binary odd detector: `F=Σm(1,3,5,7,9,11,13,15)=D`, the LSB. For Gray input `G3G2G1G0`, binary LSB=`G3⊕G2⊕G1⊕G0`.

### Q4

**(a)** Let state be Q1Q0. For `00→01→11→10→00`: `J1=Q0`, `K1=Q0'`, `J0=Q1'`, `K0=Q1`.

**(b)** Ring sequence=`1000,0100,0010,0001`; n FFs→n states. Johnson sequence=`0000,1000,1100,1110,1111,0111,0011,0001`; n FFs→2n states.

## Mock Paper B

### Q1

**(a)** 8-bit `37=00100101`; `52=00110100`; 2's comp of 52=`11001100`; sum=`11110001`. It is negative; complement gives magnitude 15, so answer `−15`.

**(b)** `ΠM(0,2,5,7,8,10)+d(1,9) → F=(B+D)(A+B'+D')`.

**(c)** `(XY)'=X'+Y'`, `(X+Y)'=X'Y'`; `[A(B+C')]'=A'+B'C`.

### Q2

**(a)** With selects AB: `I0=C`, `I1=C'`, `I2=0`, `I3=1`.

**(b)** Let `E1=A1 XNOR B1`: `A>B=A1B1'+E1A0B0'`; `A=B=E1(A0 XNOR B0)`; `A<B=A1'B1+E1A0'B0`.

### Q3

**(a)** Correction `K=C4+S3S2+S3S1`; when K=1, second adder adds `0110`. `8+7`: `1000+0111=1111`; plus `0110` gives `1 0101` → BCD 15.

**(b)** Four full adders; each B passes through XOR with M; LSB carry-in=M. M=0 adds; M=1 subtracts using 2's complement.

### Q4

**(a)** JK→D: desired `Q+=D`; excitation simplification gives `J=D`, `K=D'`.

**(b)** SISO/SIPO/PISO/PIPO meanings are above. Assuming new bits enter left, states are `0000→1000→0100→1010→1101`.

## high-probability backup answers

1. Full subtractor using decoder, variable order `A,B,Bin`: `D=Σm(1,2,4,7)`; `Bout=Σm(1,2,3,7)`.
2. Full adder using two 4:1 MUXes with AB selects: Sum inputs=`[Cin,Cin',Cin',Cin]`; Carry inputs=`[0,Cin,Cin,1]`.
3. BCD subtractor: form 10's complement of subtrahend, BCD-add it, discard end carry for positive result; without carry, complement result and mark negative.
4. Four-bit subtractor is the mode-controlled adder: `A+(B XOR M)+M`, with M=1.
5. Priority encoder: `Y1=D3+D2`, `Y0=D3+D2'D1`, `V=D3+D2+D1+D0`.
6. BCD→Excess-3 equations are in section 6 above.
7. Synchronous MOD-6 D design equations are in counter solution 7 above.
8. D→T: `D=T⊕Q`; T→D: `T=D⊕Q`.
9. Race-around answer is in flip-flop solution 6.
10. Asynchronous: ripple clocks, simple but slower; synchronous: common clock, faster but needs more logic.
