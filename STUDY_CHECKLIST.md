# complete syllabus ticklist

Tick a topic only when u can explain the rule and solve at least one basic question without notes.

**Current status:** topics 1–4, BCD adder/subtractor and flip-flop conversion are completed; topics 5–8 are mostly done; all four main flip-flop tables, equations and excitation tables are done. Only a few FF timing/control ideas remain. Current cram plan skips registers/counters.

# 1. number systems, codes and complements ✅

- [x] Binary, octal, decimal and hexadecimal systems
- [x] Integer and fractional base conversions
- [x] Binary ↔ octal/hex grouping shortcuts
- [x] General `(r−1)`'s and `r`'s complements
- [x] 1's and 2's complements
- [x] 9's and 10's complements
- [x] Subtraction using complements
- [x] Sign-magnitude representation of negative numbers
- [x] Signed 1's-complement representation and range
- [x] Signed 2's-complement representation, range and overflow
- [x] BCD, Excess-3 and Gray codes
- [x] Binary ↔ Gray conversion
- [x] Parity basics
- [ ] Final practice question completed

# 2. Boolean algebra ✅

- [x] Basic AND, OR and NOT laws
- [x] Identity, null, idempotent and complement laws
- [x] Commutative, associative and distributive laws
- [x] Absorption and redundancy/consensus theorem
- [x] De Morgan's theorems
- [x] Duality principle
- [x] Positive and negative logic, if taught
- [x] SOP and POS
- [x] Minterms and maxterms
- [x] Minimal and canonical forms
- [x] Canonical SOP/POS from a truth table
- [x] NAND and NOR as universal gates
- [ ] Final practice question completed

# 3. K-map minimization ✅

- [x] Gray-code cell ordering
- [x] 2-, 3- and 4-variable K-maps
- [x] SOP by grouping 1s
- [x] POS by grouping 0s
- [x] Pair, quad and octet groups
- [x] Edge wrapping and corner groups
- [x] Overlapping groups
- [x] With don't-care terms
- [x] Without don't-care terms
- [x] Prime and essential prime implicants
- [ ] Final practice question completed

# 4. tabulation / Quine–McCluskey ✅

- [x] Grouping minterms by number of 1s
- [x] First and later combining rounds
- [x] Dash notation
- [x] Finding prime implicants
- [x] Prime-implicant chart
- [x] Essential prime implicants
- [x] SOP with and without don't-cares
- [x] POS through minimization of `F'`
- [x] POS with and without don't-cares
- [ ] Final practice question completed

# 5. encoder, decoder, MUX and DEMUX — in progress

- [x] Encoder meaning and truth table
- [x] Decoder meaning and truth table
- [ ] Implementing a function using a decoder
- [x] MUX meaning, truth table and output equation
- [x] Implementing a function using a MUX with all variables as selects
- [x] Implementing a function using a MUX with `n−1` selects and inputs `0,1,X,X'`
- [x] DEMUX meaning, truth table and equations
- [x] Difference between decoder and DEMUX
- [x] Applications of encoder, decoder, MUX and DEMUX
- [x] Full adder/subtractor using MUX, decoder or DEMUX if taught
- [ ] Final practice question completed

# 6. code converters

- [x] General design procedure: truth table → K-maps → circuit
- [x] BCD-to-Excess-3 converter
- [x] Excess-3-to-BCD converter
- [x] Binary-to-Gray converter
- [x] Gray-to-binary converter
- [x] Detecting odd/even values from binary or Gray-code input
- [x] 4-bit binary-to-BCD converter
- [ ] Using invalid code words as don't-cares
- [ ] Final practice question completed

# 7. magnitude comparator and priority encoder

- [x] 1-bit magnitude comparator truth table
- [x] Equations for `A>B`, `A=B`, `A<B`
- [x] 2-bit/multi-bit comparison from MSB first
- [ ] Cascading comparators
- [x] Need for a priority encoder
- [x] 4-to-2 priority-encoder truth table
- [x] Priority-encoder output equations
- [x] Valid output bit
- [ ] Final practice question completed

# 8. binary adder and subtractor

- [x] Half-adder truth table and equations
- [x] Full-adder truth table and equations
- [x] Full adder using two half adders
- [ ] 4-bit ripple-carry/parallel binary adder
- [x] Half-subtractor truth table and equations
- [x] Full-subtractor truth table and equations
- [ ] 4-bit ripple-borrow binary subtractor
- [x] 4-bit parallel adder-subtractor using mode M, XOR gates and full adders
- [x] Signed overflow rule
- [ ] Final practice question completed

# 9. BCD adder and subtractor

- [x] BCD addition procedure
- [x] Detecting an invalid BCD sum
- [x] Correction condition `K=C4+S3S2+S3S1`
- [x] Adding `0110` correction
- [x] Multi-digit decimal carry
- [x] BCD subtraction using 10's complement
- [x] BCD subtraction using 9's complement/end-around carry
- [x] BCD adder/subtractor block diagram
- [ ] Final practice question completed

# 10. flip-flops

- [ ] Meaning of clock, present state and next state
- [x] SR truth/characteristic table and invalid state
- [x] JK truth/characteristic table
- [x] D truth/characteristic table
- [x] T truth/characteristic table
- [x] Characteristic equations
- [x] Combined excitation table
- [ ] Preset and clear
- [ ] Level-triggered versus edge-triggered operation
- [ ] JK race-around and its solutions
- [ ] Master-slave flip-flop, if taught
- [ ] Final practice question completed

# 11. registers

- [ ] Register and shift-register basics
- [ ] SISO
- [ ] SIPO
- [ ] PISO
- [ ] PIPO
- [ ] State after each clock pulse
- [ ] Left shift versus right shift
- [ ] Bidirectional shift register, if taught
- [ ] Universal shift-register operations
- [ ] Applications of registers
- [ ] Final practice question completed

# 12. synchronous and asynchronous counter design

- [ ] Modulus and number of required flip-flops
- [ ] Asynchronous/ripple counter operation
- [ ] Ripple delay and frequency division
- [ ] Synchronous counter operation
- [ ] Synchronous binary up-counter equations
- [ ] Synchronous binary down-counter equations
- [ ] Counter design using state and excitation tables
- [ ] Counter design using D flip-flops
- [ ] Counter design using JK/T flip-flops
- [ ] Truncated/MOD-N counter
- [ ] Unused states and self-starting operation
- [ ] Final practice question completed

# 13. ring and twisted-ring/Johnson counters

- [ ] Ring-counter circuit and direct feedback
- [ ] Ring-counter state sequence
- [ ] Ring counter has n states for n flip-flops
- [ ] Ring-counter initialization/all-zero lock
- [ ] Johnson-counter circuit and complemented feedback
- [ ] Johnson-counter state sequence
- [ ] Johnson counter has `2n` states
- [ ] Comparison between ring and Johnson counters
- [ ] Final practice question completed

# 14. conversion of flip-flops

- [x] Meaning of available FF versus desired FF
- [x] General conversion-table procedure
- [x] JK → D
- [x] JK → T
- [x] D → JK
- [x] D → T
- [x] T → D
- [x] SR → D
- [x] At least one conversion derived using a K-map
- [ ] Final practice question completed

# possible extra: FSM — only if officially confirmed

FSM was not written on the syllabus image, so do not prioritize it unless your teacher confirms it.

- [ ] FSM confirmed as part of syllabus
- [ ] State diagram and state table
- [ ] Mealy versus Moore machine
- [ ] State reduction/assignment, if included
- [ ] FSM design using flip-flops, if included

# final readiness

- [ ] Attempted `LAST_YEAR_STYLE_PRACTICE.md` Mock Paper A in 90 minutes
- [ ] Corrected every mistake after the mock
- [ ] Rewritten all essential formulas/tables from memory
- [ ] Reviewed the final five-minute scan in `PRACTICE_QUESTIONS.md`
