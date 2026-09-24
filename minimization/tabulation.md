# tabulation / quine–mccluskey method

This minimizes Boolean functions like a K-map, but uses tables instead of boxes. It is longer, but works when there are too many variables for an easy K-map.

# SOP procedure

## 1. list terms

write minterms in binary and group by count of 1s. include don't-cares for combining, but mark em `d`.

## 2. combine adjacent groups

compare group 0 ones with group 1, group 1 with group 2, etc. combine terms differing in **exactly one bit** and replace changed bit with `-`.

example: `0101` + `0111` → `01-1`.

Put a check mark beside every term that was combined. Repeat the same process with the new dash terms until no more combinations are possible. Remove repeated copies each round.

## 3. prime implicants

any term that could not combine further is a PI. decode pattern:

`1-0-` for variables `ABCD` → `AC'`.

## 4. PI chart

columns = required minterms (**do not make columns for don't-cares**). rows = PIs. put X where PI covers minterm.

- column with only one X → that row is essential; select it
- cross out all columns it covers
- cover leftovers using minimum rows/literals

If several choices remain, choose the set using the fewest terms/literals. A formal method called Petrick's method can do this, but use it only if your class specifically taught it.

# POS using tabulation

clean method: minimize `F'` as SOP using the **zero indices of F**, then complement final answer with De Morgan.

example: if `F' = A'B + C`, then `F = (A+B')C'`.

for POS don't-cares: include the same don't-care indices while minimizing `F'`; they can help combining but never need chart coverage.

# tiny worked combining example

`F(A,B,C)=Σm(1,3,5,7)`:

`001,011,101,111` combine until pattern `--1`, so `F=C`.

# traps

- two terms combine only when they differ in exactly one fixed bit
- `0-1` and `1-1` combine to `--1`; dash positions must match
- dont-care helps create PIs but does not have to be covered
- uncombined term from **every round** can be a PI; dont only inspect final round
- POS is not obtained by simply replacing plus signs; minimize F' then complement properly
