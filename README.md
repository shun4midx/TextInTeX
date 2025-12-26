# TextInTeX

A mini project library that turns text-based LaTeX and natural notation into copy-pasteable, natural-looking mathematical **plain text**.

... In other words, it allows you to text in TeX.

I plan to perhaps have libraries in C++ and Python as per usual, and maybe extend this to a Discord bot and to be hosted on a website.

## Why TextInTeX?
 - LaTeX is powerful but not copy-paste friendly
 - Plain text math (e.g. 1/2, (x+1)/y, sum_{i=0}^n x^i) loses structure
 - Unicode can express more math, if used carefully

## Conversions and Rules

Key Philosophy:
> TextInTeX only uses Unicode superscripts/subscripts when every required glyph exists, otherwise expressions are rendered on the baseline. However, I will try my best to accommodate as many mathematical notations possible, since TextInTeX is supposed to make typing math as easy as possible.

TextInTeX plans to offer the main functions: `convert_natural(math_text, bool inline)`, `convert_latex(math_text, bool inline)`, and `convert(text, bool inline)`, with `inline` defaulted to `false`. When `inline = false`, TextInTeX may promote fractions to multi-line layout when inline
rendering would reduce structural clarity.

`convert()` is different in the sense that, you can type not just math in your text. It functions by detecting your **delimiters**, where you can wrap your mathematical text around.
 - `@@[math]@@`: Natural-mode math conversion
 - `$$[math]$$`: LaTeX-mode math conversion
 - `@@@[math]@@@`: FORCE-INLINE Natural-mode math conversion
 - `$$$[math]$$$`: FORCE-INLINE LaTeX-mode math conversion

Due to the philosophy to make typing math as easy as possible, I support natural fraction notation in LaTeX notation as well, e.g. `$$1/2$$` is also acceptable in addition to `$$\frac{1}{2}$$`!

## Design Guarantees

- TextInTeX never uses Unicode glyphs that do not exist.
- Superscripts/subscripts are only used when fully supported.
- Inline output never sacrifices structural clarity.
- Multi-line layout is used only when necessary.
- All output is plain-text and copy-pasteable.

## Examples
Input 1: `@@1/2@@`

Output 1: `¹⁄₂`

Input 2: `@@(1+3)/23@@`

Output 2:
```
 1+3
-----
 23
```

Input 3: `@@@(1+3)/23@@@`
 
Output 3: `(1+3)/23` (Since `@@@...@@@` forces it to be inline)

Input 4: `$$\int_0^1 x^2 dx$$`

Output 4: `∫₀¹ x² dx`

Input 5: `@@sum i=0..inf (1/2)^i@@`

Output 5: `Σᵢ₌₀^∞ (¹⁄₂)ⁱ`

# All Available Mathematical Notations
Documentation in progress

# What if I want to suggest new math displays for TextInTeX?

Please contact me in any language I said is fine in [my GitHub home page](https://github.com/shun4midx#languages), via [Email](mailto:shun4midx@gmail.com) or Discord at @shun4midx, or open an Issue.

You must detail:
 - What your mathematical symbol is
 - How it should be supported in "Natural" mode and "LaTeX" mode
 - Most importantly **the corresponding unicode symbol(s) required for this usage case, and a valid mathematical example of using this symbol with only unicode symbols**. 
 
I may add it if it aligns with the project philosophy and I have the capacity to do so. If I decide to add it, I will notify you, and perhaps continue the conversation for more details if I face any confusion.

## Planned Functionalities
- Block-mode matrix rendering (limited rows/columns)

## Non-goals (Since this defeats the philosophy of TextInTeX)
- Full LaTeX layout rendering
- Arbitrary 2D math typesetting
- Font-dependent visual hacks

# License
MIT License, reference `LICENSE` for more information.