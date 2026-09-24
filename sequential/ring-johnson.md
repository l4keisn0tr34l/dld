# ring counter

A ring counter is a shift register arranged in a loop: the last output is connected directly back to the first input. Usually one `1` keeps moving around the loop.

start with one-hot seed, e.g. 4-bit `1000`:

`1000 → 0100 → 0010 → 0001 → 1000`

- n flip-flops → n useful states (MOD-n)
- one output active at a time, easy decoding
- must initialize one 1; all-zero state stays stuck at zero

# johnson / twisted-ring counter

A Johnson counter is almost the same, but feeds the **opposite/complement** of the last output back to the first. This creates twice as many useful states as a ring counter.

one possible 4-bit sequence:

`0000 → 1000 → 1100 → 1110 → 1111 → 0111 → 0011 → 0001 → 0000`

(direction/order can reverse based on drawing; state count stays same.)

- n flip-flops → `2n` useful states
- wave of 1s fills register, then wave of 0s empties it
- decoding is easier than binary counters

## compare

| property | ring | Johnson |
|---|---|---|
| feedback | Qlast | Qlast' |
| valid states with n FF | n | 2n |
| typical init | one-hot | all zero works |
| efficiency | low | better |

## finding state sequence from a circuit

1. copy current Q values
2. compute first FF's D from feedback wire
3. shift every old Q to next FF **simultaneously**
4. write new state after clock

never update one FF at a time using already-updated values; all flip-flops sample old state together.
