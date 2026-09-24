# flip-flops

A flip-flop is a tiny memory cell that stores one bit. Its current stored bit is called `Q`; the value after the next clock is `Q(next)` or `Q+`.

A combinational circuit has no memory. A sequential circuit, such as a flip-flop, uses current inputs **and the value already stored**.

## clock words

- **clock:** repeating timing signal telling the flip-flop when it may update
- **edge-triggered:** changes only at the instant the clock rises or falls
- **preset/set:** forces Q=1; **clear/reset:** forces Q=0 (often without waiting for clock)
- `Q'` should be opposite of Q

## characteristic tables (what next state happens)

### SR

| S R | Q(next) |
|---|---|
| 00 | Q (hold) |
| 01 | 0 |
| 10 | 1 |
| 11 | invalid |

characteristic equation: `Q+ = S + R'Q` (with SR≠11).

### JK

| J K | Q(next) |
|---|---|
| 00 | Q |
| 01 | 0 |
| 10 | 1 |
| 11 | Q' (toggle) |

`Q+ = JQ' + K'Q`. JK fixes SR invalid state by toggling at 11.

### D

`Q+ = D`. literally stores the input bit.

### T

| T | Q(next) |
|---|---|
| 0 | Q |
| 1 | Q' |

`Q+ = T⊕Q`.

# excitation tables (what input u need for desired transition)

X means dont-care.

| Q→Q+ | SR | JK | D | T |
|---|---|---|---|---|
| 0→0 | 0X | 0X | 0 | 0 |
| 0→1 | 10 | 1X | 1 | 1 |
| 1→0 | 01 | X1 | 0 | 1 |
| 1→1 | X0 | X0 | 1 | 0 |

**characteristic = input tells next state. excitation = state transition tells required input.**

## race around in JK

in level-triggered JK, when J=K=1 and clock pulse stays active longer than propagation delay, Q toggles repeatedly. avoid using edge-triggered/master-slave FF or short clock pulse.
