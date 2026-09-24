# encoder, decoder, mux, demux

These are all combinational circuits, meaning they do not remember an old value.

## decoder

`n` input bits → up to `2^n` output lines. Exactly one output is selected for each input number (when the enable switch is on).

2-to-4 active-high decoder:

| AB | active output |
|---|---|
| 00 | `Y0=A'B'` |
| 01 | `Y1=A'B` |
| 10 | `Y2=AB'` |
| 11 | `Y3=AB` |

so decoder outputs are minterms. application: memory/address selection and implementing functions by OR-ing needed outputs.

## encoder

reverse idea: `2^n` input lines → n-bit code. ordinary encoder assumes exactly one input active.

8-to-3: if `D5=1`, output is binary 5 = `101`.

if multiple inputs can be 1, normal encoder is ambiguous → use priority encoder.

## multiplexer (MUX)

many data inputs → **one output**. A MUX is like a digital selector switch: select lines decide which one input reaches the output.

4:1 MUX has data `I0..I3`, 2 selects `S1S0`:

`Y=I0S1'S0' + I1S1'S0 + I2S1S0' + I3S1S0`.

application: data selection and implementing Boolean functions.

### function using a MUX

use some variables as selects. for each select combination, inspect function versus leftover variable X and set corresponding data input to `0,1,X,or X'`.

## demultiplexer (DEMUX)

**one data input** → many outputs. A DEMUX does the reverse routing: select lines decide which one output receives D; all others stay inactive.

1:4 DEMUX:

- `Y0=DS1'S0'`
- `Y1=DS1'S0`
- `Y2=DS1S0'`
- `Y3=DS1S0`

application: routing one data source to destinations.

## dont mix em up

- decoder: code in, one-hot out; no real data input (apart from enable)
- DEMUX: one data in, routed output
- encoder: one-hot in, code out
- MUX: selected data in, one output

**MUX = many to one. DEMUX = one to many.**
