# registers

A register is a row of flip-flops used to store or move a binary number. They share one clock so they update together. Since one flip-flop stores one bit, n bits need n flip-flops.

## four basic types

| type | input | output | what it does |
|---|---|---|---|
| SISO | serial | serial | bits enter/leave one per clock |
| SIPO | serial | parallel | serial-to-parallel conversion |
| PISO | parallel | serial | parallel-to-serial conversion |
| PIPO | parallel | parallel | load/read full word together |

## shift register

At every active clock edge, each flip-flop sends its old bit to the next flip-flop. All movement happens together. The wiring decides left/right direction. Serial input enters one bit at a time; serial output leaves one bit at a time.

for a 4-bit SIPO initially `0000`, shifting bits `1,0,1,1` takes 4 clock edges before complete word is available (exact displayed order depends on shift direction).

## controls

- clear: make all bits 0
- load: accept parallel data
- shift left/right: move data one position
- hold: retain current word

universal shift register can hold, shift left, shift right and parallel-load, usually selected by two control lines.

## uses

temporary storage, delay line, serial/parallel conversion, arithmetic shifts, and ring/Johnson counters.

## trap

register contents change on clock events, not continuously. be consistent about whether diagram shifts toward Q0 or Q3; dont assume direction from the phrase alone.
