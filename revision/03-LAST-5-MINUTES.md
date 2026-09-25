# last five-minute scan

Read every line once. These are the mistakes most likely to cost easy marks.

- In Boolean algebra, `+` means OR, not normal addition.
- Dual means swap AND↔OR and 0↔1. Do not complement variables.
- Complement means apply NOT and use De Morgan.
- SOP groups K-map 1s; POS groups K-map 0s.
- Minterms come from output-1 rows; maxterms come from output-0 rows.
- K-map order is `00,01,11,10`, not ordinary binary order.
- K-map edges touch, corners touch, diagonals do not.
- Legal group size is 1,2,4,8... Never 3 or 6.
- Don't-care X is optional; use it only if it helps.
- In tabulation, combine terms differing in exactly one bit.
- Don't-care terms do not need PI-chart columns.
- MUX = many-to-one. DEMUX = one-to-many.
- Decoder code selects an output; DEMUX routes data D.
- Priority encoder chooses the highest active input.
- Larger comparator checks MSB first.
- Half adder/subtractor has no carry/borrow input. Full version does.
- Full-adder sum and full-subtractor difference are both three-input XOR.
- Four-bit adder means four full adders with carry chained.
- Adder-subtractor uses `A+(B XOR M)+M`.
- BCD uses each decimal digit separately.
- BCD result above 9 or with carry needs `+0110`.
- For 10's-complement subtraction: carry means positive; no carry means complement and make negative.
- SR input 11 is invalid.
- JK input 11 toggles.
- D simply stores D.
- T=1 toggles.
- Characteristic table: inputs tell u next state.
- Excitation table: desired state change tells u required inputs.
- Bubble on an input usually means active-low.
- Triangle on FF clock means edge-triggered.
- Label every circuit input, output, carry/borrow and mode line.
- For a design answer, show: truth/state table → equation/K-map → final circuit.

# if panic hits

Start with what is known, write the truth table, then derive. Even an incomplete labelled table, correct formula, and partial circuit can earn marks. Do not leave a design question blank.
