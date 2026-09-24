# Digital Logic Exam Prep — Context

Source: Neso Academy "Digital Electronics" playlist (https://www.nesoacademy.org/ec/05-digital-electronics), mapped against a handwritten syllabus with 14 numbered topics.

## Your Syllabus (14 items)
1. Number Systems & Codes & their N's / (N-1)'s Complement
2. Boolean Algebra
3. K-map minimization in SOP & POS, with & without don't-care terms
4. Tabulation Method (both SOP & POS), with & without don't-care terms
5. Encoder, Decoder, MUX, DEMUX & their applications
6. Code Converters (BCD to Excess-3, 4-bit binary to BCD, etc.)
7. Magnitude Comparator, Priority Encoder
8. Binary Adder & Subtractor
9. BCD Adder & Subtractor
10. Flip-Flops
11. Registers
12. Sync & Async Counter design
13. Ring Counter & Twisted Ring (Johnson's) Counter
14. Conversion of Flip-Flops

## Chapters to Watch (Neso Academy)
- Ch 2 Boolean Algebra
- Ch 3 Number Systems
- Ch 4 Codes
- Ch 5 Logic Gates
- Ch 6 Logic Minimization (K-map + Tabulation)
- Ch 7 Combinational Circuits (biggest chapter — MUX/DEMUX/encoders/decoders/comparator/adder-subtractor)
- Ch 8 Flip Flops
- Ch 10 Counters
- Ch 11 Registers

**Skip:** Ch 1 (Intro — optional review only), Ch 9 (Design at RTL), Ch 12 (Programmable Logic Devices) — not on syllabus.

## Gaps in the Neso Playlist (need outside sources)
- **Code converters (BCD↔Excess-3, etc., syllabus #6):** weakly covered — Neso has the codes themselves but not clean circuit-design (K-map) walkthroughs for converters.
  - GeeksforGeeks: https://www.geeksforgeeks.org/?p=162029 (full K-map derivation, BCD↔Excess-3)
  - YouTube: search "BCD to Excess-3 Converter Design" (Dhiman Kakati, ~14 min)
- **BCD Adder/Subtractor (syllabus #9):** BCD Adder likely exists as a standalone Neso video ("BCD Adder | Simple Explanation") — search that exact title on YouTube. BCD Subtractor is not on Neso.
  - Hackatronic: https://hackatronic.com/?p=7235 (9's complement method, correction logic)
  - Backup: Unacademy GATE ECE lesson — https://unacademy.com/lesson/bcd-adder/NFZSIHA3
- **Tabulation method for POS + don't-cares (syllabus #4):** Neso has only one Quine-McCluskey video; unconfirmed if it covers POS/don't-care. Check it first, search "Quine-McCluskey POS don't care" if it doesn't.

## Chapter-Relative Time Budget (est., ~21h total for full syllabus scope)
| Chapter | Est. Time |
|---|---|
| Boolean Algebra | ~2h 20min |
| Number Systems | 3h 15min (confirmed) |
| Codes | ~1h 25min |
| Logic Gates | ~1h |
| Logic Minimization | ~1h 40min |
| Combinational Circuits | ~5h+ (longest, most varied) |
| Flip Flops | ~3h 30min |
| Counters | ~1h 40min |
| Registers | ~1h |

## Compressed Plan for Limited Time (~8-9h budget)
**Tier 1 — watch fully (~5.5h):**
- Boolean Algebra: only Minimal↔Canonical Form (Pt 1&2), SOP/POS Examples, Positive/Negative Logic, Dual Form, Complement Meaning, Boolean Algebra Problems (Pt 1&2)
- Number Systems: base conversions (decimal/binary/octal/hex, all directions) + r's/(r-1)'s/1's/2's complement + binary addition/subtraction + complement-based subtraction (skip octal/hex arithmetic, multiplication/division, signed magnitude/complement data representation)
- Logic Minimization: full chapter (K-map + Tabulation)
- Flip Flops: SR/D/JK/T intro + truth/characteristic/excitation tables + all 4 FF conversions (skip state machines, Mealy/Moore, ASM charts — not on syllabus)

**Tier 2 — watch at 1.5-2x speed (~1h effective):**
- Logic Gates (mostly review)
- Counters: sync/async design + Ring/Johnson's counter (trim extras)
- Registers: SISO/SIPO/PIPO/PISO basics (skip bidirectional/universal shift register)

**Tier 3 — skip video, read instead:**
- Combinational Circuits: watch only MUX/DEMUX intro, Encoders/Decoders, Priority Encoder, Comparator, Adder/Subtractor (~1h) — skip "implement X using Y MUX" variants and practice-problem videos
- Codes: read a cheat sheet on BCD/Excess-3/Gray/parity instead of watching (~15 min)
- Code converter + BCD subtractor gaps: read the linked articles instead of hunting videos (~10 min)

**If still over budget:** cut Registers to shift-register modes only; cut Counters to sync-vs-async + ring counter only.

## Skip List (confirmed not worth watching, low ROI vs syllabus)
- Self Dual, Venn Diagram, Switching Circuits (Boolean Algebra extras)
- Binary Multiplication/Division
- Octal & Hex Addition/Subtraction/Multiplication
- Data Representation (Signed Magnitude/1's/2's Complement) — only relevant if your course frames subtractor circuits as complement-based addition
