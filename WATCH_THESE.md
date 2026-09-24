# stuff u should actually watch instead of only reading

not saying these are impossible, but theyre visual/procedural and text alone is a bad bargain. read the matching note first, then watch one solved example and redo it yourself.

## absolutely watch

### 1. K-map grouping — syllabus #3

need to see wraparound groups, overlapping, SOP vs POS and don't-cares drawn on the map.

watch in Neso **Ch 6 Logic Minimization**: K-map videos. then solve one 4-variable SOP and one POS without the video.

### 2. tabulation / Quine–McCluskey — syllabus #4

multiple combining rounds + PI chart are hard to understand from prose.

watch Neso's tabulation video first. if it skips POS/don't-cares, search YouTube: **“Quine McCluskey POS don't care solved example”**. POS trick: minimize F' from zero indices, then complement.

### 3. synchronous counter design — syllabus #12

this combines state tables, FF excitation tables, K-maps and circuits. watch at least one full arbitrary-sequence counter design, not only a binary counter animation.

search: **“synchronous counter design using JK flip flop excitation table”**. use `sequential/counters.md` as checklist.

### 4. flip-flop conversion — syllabus #14

watch one complete conversion table derivation. after that all conversions use same recipe.

Neso Ch 8 has all four FF conversions. prioritize **JK↔D** and **JK↔T**, then practice one yourself.

## strongly recommended

### BCD adder/subtractor — syllabus #9

correction `+0110`, decimal carry and complement subtraction make more sense with a worked circuit.

- YouTube search exact title: **“BCD Adder | Simple Explanation Neso Academy”**
- BCD subtractor reading: https://hackatronic.com/?p=7235

### code-converter circuit design — syllabus #6

the codes are easy; making four K-maps from a truth table is the part worth seeing.

- walkthrough: https://www.geeksforgeeks.org/?p=162029
- YouTube search: **“BCD to Excess-3 Converter Design Dhiman Kakati”**

### MUX implementation of Boolean functions — syllabus #5

watch one example where n-1 variables are selects and data inputs become `0,1,X,X'`. skip ten near-identical variants after u can do one alone.

## animations worth a quick look

- ripple vs synchronous counter timing
- SISO/SIPO/PISO shifting per clock
- ring vs Johnson feedback sequence
- JK race-around and master-slave FF

Neso chapters: Ch 8 Flip Flops, Ch 10 Counters, Ch 11 Registers.

## dont waste video time on

basic code definitions, truth tables of simple gates, repeated base-conversion sums, or ten variations of the same MUX question. those are faster from the markdown notes + practice.
