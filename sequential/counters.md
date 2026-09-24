# counters

A counter moves through a fixed sequence of binary states whenever clock pulses arrive. An n-bit counter can have up to `2^n` states. **Modulus (MOD)** means how many states occur before the sequence repeats.

number of FFs needed for MOD-N: smallest n such that `2^n ≥ N`, i.e. `ceil(log₂N)`.

# asynchronous / ripple counter

Only the first flip-flop receives the main clock. Its output clocks the next flip-flop, and so on—like a ripple moving through water. Usually T=1 or J=K=1, so each stage toggles.

- easy, fewer gates
- propagation delay accumulates, so outputs briefly pass through false states
- divide-by-2 per stage; n stages divide clock by `2^n`

# synchronous counter

All flip-flops receive the same clock at the same time. Extra logic decides which ones toggle. This is faster because the clock does not ripple through them one by one.

for synchronous binary **up** counter using T FFs:

- `T0=1`
- `T1=Q0`
- `T2=Q1Q0`
- generally bit i toggles when all lower bits are 1

for down counter, bit i toggles when all lower bits are 0 (use complemented lower Qs).

# design a synchronous custom counter

1. determine number of FFs
2. write desired state sequence/table: present state → next state
3. include unused states; choose recovery transitions or mark don't-care only if allowed
4. use excitation table for chosen FF to find required input in every row
5. K-map each FF input separately
6. draw common-clock circuit

with D FF it is easiest: each `Di = Qi(next)`.

# truncated / MOD-N ripple counter

use n FFs where `2^n≥N`; decode state N and asynchronously clear to 0. example MOD-10 detects binary 1010 and resets. due to delays, decoded-reset circuits can glitch.

## exam traps

- async vs sync refers to FF clocking, not whether reset pin is asynchronous
- unused states should ideally return to valid sequence (self-starting)
- frequency division works cleanly for full binary ripple stages
- maximum count of n-bit up counter is `2^n-1`, but number of states is `2^n`
