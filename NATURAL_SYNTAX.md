# TextInTeX Natural Syntax
This document describes the supported input syntax for **Natural Mode** (`@@ ... @@`). It is intentionally limited and prioritizes readability, ease of typing, and unambiguous structure.

### Terminology

**Atomic expression**  
A single symbol or number without internal structure (e.g. `1`, `x`, `x²`, `aₙ`).


## Numbers and Symbols
- Integers and decimals are supported: `1`, `23`, `3.14`
- Greek letters may be written by name: `alpha`, `theta`, `pi`
- Variables other than Greek letters are single letters: `x`, `n`, `i`

## Superscripts and Subscripts
- Superscripts use `^`
- Subscripts use `_`
- Braces may be omitted for single atoms

Examples:

| Natural Syntax  | Output      |
| --------------- | ----------- |
| `@@x^2 + y^2@@` | x² + y²     |
| `@@theta/2@@`   | ᶿ⁄₂         |
| `@@x^(n+1)@@`   | xⁿ⁺¹        |
| `@@a_i@@`       | aᵢ          |

## Fractions

Fractions are written using `/`.

- Atomic fractions may be rendered inline
- Structural fractions may be promoted to multi-line layout
- Nested fractions are always rendered inline

Examples:

| Natural Syntax  | Output          |
| --------------- | --------------- |
| `@@1/2@@`       | ¹⁄₂             |
| `@@1/x@@`       | ¹⁄ₓ             |
| `@@(1+3)/23@@`  | block layout    |
| `@@@(1+3)/23@@@`| (1+3)/23        |

The block layout fraction is as follows:

```
 1+3
-----
 23
```

## Sums, Integrals, and Ranges

Summations can be written using natural syntax:

`sum <var>=<lower>..<upper> <expr>`

Integrals can be written using natural syntax:

`int <lower>..<upper> <expr> d<variable>`

Examples:
| Natural Syntax            | Output          |
| ------------------------- | --------------- |
| `@@sum i=0..inf (1/2)^i@@`| Σᵢ₌₀^∞ (¹⁄₂)ⁱ   |
| `@@int a..b e^x dx@@`     | ∫ₐᵇ eˣ dx       |

## Non-goals
- This is NOT a full programming language
- This syntax may evolve
- Unsupported expressions fall back to baseline rendering