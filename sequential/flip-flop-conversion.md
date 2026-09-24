# conversion of flip-flops

Conversion does not physically turn one flip-flop into another. We add logic at its inputs so the flip-flop we **have (available)** behaves like the type we **want (desired)**.

## method that always works

1. make a table containing current value Q and the desired flip-flop's inputs
2. use the desired flip-flop's characteristic table to find what `Q(next)` must be
3. use the **available flip-flop's excitation table** to find what inputs will cause `Q→Q(next)`
4. K-map each available input using desired inputs + Q as variables
5. connect simplified logic before available FF

X entries in excitation table are free don't-cares and help simplify.

## useful direct conversions

### JK behaves as D

need `Q+=D`; choose:

`J=D`, `K=D'`.

### JK behaves as T

`J=T`, `K=T`.

### D behaves as T

since D equals next state:

`D=T⊕Q`.

### D behaves as JK

feed D the JK characteristic equation:

`D=JQ' + K'Q`.

### T behaves as D

T is 1 exactly when desired D differs from present Q:

`T=D⊕Q`.

### SR behaves as D

`S=D`, `R=D'` (never produces invalid 11).

## general shortcut

if available FF is D: input is simply desired characteristic equation.

if available FF is T: `T = Q⊕Q(next)`.

for JK/SR, use excitation table rather than guessing because dont-cares usually simplify result.

## trap

wording matters: “convert JK to D” normally means **JK is hardware available**, D is behavior wanted. circuit inputs must therefore be J and K. always label available vs desired before starting.
