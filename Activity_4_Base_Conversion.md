# Activity 4 – Base Conversion Laboratory

## Station 5: My Number

**Student ID:** 26128352

N = last three digits of student ID = **352**. Since N is not below 100, use N = 352.

---

## 1. Binary conversion (base 2)

Repeated division by 2. Read the remainders from bottom to top.

| Dividend ÷ 2 | Quotient | Remainder |
|---|---|---|
| 352 ÷ 2 | 176 | 0 |
| 176 ÷ 2 | 88 | 0 |
| 88 ÷ 2 | 44 | 0 |
| 44 ÷ 2 | 22 | 0 |
| 22 ÷ 2 | 11 | 0 |
| 11 ÷ 2 | 5 | 1 |
| 5 ÷ 2 | 2 | 1 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

**Final answer:** 352₁₀ = **101100000₂**

## 2. Octal conversion (base 8)

Repeated division by 8. Read the remainders from bottom to top.

| Dividend ÷ 8 | Quotient | Remainder |
|---|---|---|
| 352 ÷ 8 | 44 | 0 |
| 44 ÷ 8 | 5 | 4 |
| 5 ÷ 8 | 0 | 5 |

**Final answer:** 352₁₀ = **540₈**

## 3. Hexadecimal conversion (base 16)

Repeated division by 16. Read the remainders from bottom to top.

| Dividend ÷ 16 | Quotient | Remainder |
|---|---|---|
| 352 ÷ 16 | 22 | 0 |
| 22 ÷ 16 | 1 | 6 |
| 1 ÷ 16 | 0 | 1 |

**Final answer:** 352₁₀ = **160₁₆** (remainder 15 = F).

## 4. Verification by converting back to decimal

### Binary place-value table

| Binary digit | Place value | Digit × place value |
|---|---|---|
| 1 | 256 | 1 × 256 = 256 |
| 0 | 128 | 0 × 128 = 0 |
| 1 | 64 | 1 × 64 = 64 |
| 1 | 32 | 1 × 32 = 32 |
| 0 | 16 | 0 × 16 = 0 |
| 0 | 8 | 0 × 8 = 0 |
| 0 | 4 | 0 × 4 = 0 |
| 0 | 2 | 0 × 2 = 0 |
| 0 | 1 | 0 × 1 = 0 |

Sum: 256 + 0 + 64 + 32 + 0 + 0 + 0 + 0 + 0 = **352₁₀**

### Octal place-value table

| Digit | Place value | Digit × place value |
|---|---|---|
| 5 | 64 | 5 × 64 = 320 |
| 4 | 8 | 4 × 8 = 32 |
| 0 | 1 | 0 × 1 = 0 |

Sum: 320 + 32 + 0 = **352₁₀**

### Hexadecimal place-value table

| Digit | Place value | Digit × place value |
|---|---|---|
| 1 | 256 | 1 × 256 = 256 |
| 6 | 16 | 6 × 16 = 96 |
| 0 | 1 | 0 × 1 = 0 |

Sum: 256 + 96 + 0 = **352₁₀**

## 5. Grouping cross-check

- Binary: 101100000₂
- Binary → octal: 101100000₂ → 101 100 000 → **540₈**
- Binary → hexadecimal: 101100000₂ → 0001 0110 0000 → **160₁₆**

Both grouping results match the repeated-division answers.

## 6. Error analysis

The mistake is reading the remainders from top to bottom instead of from bottom to top. For 46₁₀, repeated division gives remainders 0, 1, 1, 1, 0, 1 from top to bottom; reversing them gives 101110₂. Therefore, 46₁₀ = 101110₂, not 011101₂.

---

## Final answers

**352₁₀ = 101100000₂ = 540₈ = 160₁₆**
