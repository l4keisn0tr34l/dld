# boolean algebra — final cheat sheet

Boolean algebra is normal algebra made for 0 and 1. Here `+` means OR, a dot or two letters together means AND, and `'` means NOT.

Example: `AB'` means **A AND NOT B**.

## laws u actually use

| law | result |
|---|---|
| `A+0` / `A·1` | `A` |
| `A+1` / `A·0` | `1` / `0` |
| `A+A` / `A·A` | `A` |
| `A+A'` / `AA'` | `1` / `0` |
| `(A')'` | `A` |
| `A+AB` | `A` (absorption) |
| `A(A+B)` | `A` (absorption) |
| `A+A'B` | `A+B` |
| `A(A'+B)` | `AB` |

## de morgan — very important

To remove a NOT outside brackets, **swap AND ↔ OR** and put NOT on every variable:

- `(AB)' = A'+B'`
- `(A+B)' = A'B'`

## dual

swap `+ ↔ ·` and `0 ↔ 1`. variables/complements stay untouched.

example: dual of `A+0=A` is `A·1=A`.

## SOP vs POS

- SOP = OR of product terms, naturally uses rows where `F=1`
- POS = AND of sum terms, naturally uses rows where `F=0`
- canonical means **every term contains every variable**; minimal means unnecessary literals have been removed

### write minterm from a 1-row

bit 1 → normal variable; bit 0 → complement.

`A B C = 0 1 0` gives `A'BC' = m2`.

### write maxterm from a 0-row

opposite rule: bit 0 → normal; bit 1 → complement.

`0 1 0` gives `(A+B'+C) = M2`.

`F=Σm(1,3,6)` lists the 1s. `F=ΠM(0,2,4,5,7)` lists the 0s. for the same function, the two index lists are complements.

## minimal → canonical

- missing variable in SOP product P: `P = P(X+X')`
- missing variable in POS sum S: `S = (S+X)(S+X')`

## NAND / NOR

- NAND is universal: NOT by tying inputs; AND by NAND then invert; OR by De Morgan
- NOR is universal: NOT by tying inputs; OR by NOR then invert; AND by De Morgan

## common trap

`A+B C` means `A+(BC)` because AND happens before OR. dont randomly distribute unless needed.
