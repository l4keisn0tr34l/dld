# k-map minimization

A K-map is a box diagram used to turn a long Boolean expression into a shorter one. Shorter expression = fewer/simpler gates.

this is visual, so read this for rules but watch the video listed in `WATCH_THESE.md` if grouping feels weird.

## setup

cells follow **gray order**, not normal binary:

`00, 01, 11, 10`

this makes neighboring cells differ by one variable. first and last row/column are also neighbors — map **wraps around**. diagonals are not neighbors.

## SOP: group the 1s

1. enter 1s from `Σm(...)`
2. use don't-cares `X` only if they help
3. make rectangles of size `1,2,4,8,...`
4. make groups as large as possible
5. cover every 1; overlap is allowed
6. each group gives a product term

within one group, variables that change disappear. constants remain:

- constant 1 → normal literal
- constant 0 → complemented literal

example: if A stays 1, B stays 0 and C changes, term is `AB'`.

## POS: group the 0s

same rules, but group zeroes. each group gives a sum term:

- constant 0 → normal literal
- constant 1 → complemented literal

example: A stays 1, B stays 0, C changes → `(A'+B)`.

## dont-care terms

`X` can act as 0 or 1 separately, whatever makes bigger groups. u **do not need to cover an X**, and never make a useless all-X group.

## exam terminology in simple words

- **implicant:** any legal group
- **prime implicant (PI):** a group that cannot be made any bigger
- **essential PI:** a group that covers at least one required cell no other group can cover

pick essentials first, then cheapest groups to cover leftovers.

## group priority

try in this order: octet → quad → pair → singleton. fewer/larger groups usually mean fewer literals.

## common traps

- using binary order instead of gray order
- forgetting corner group and edge wrapping
- making groups of 3, 6 etc. (illegal)
- grouping diagonally (illegal)
- aiming for zero overlap (overlap is completely fine)
- for POS, writing SOP literal rules by accident

## quick self-check

plug one original 1-row and one 0-row into final expression. also verify every required cell got covered.
