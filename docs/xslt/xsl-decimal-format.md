---
description: Indicates a set of localisation parameters
---

# xsl:decimal-format

Indicates a set of localisation parameters. If the `xsl:decimal-format` element has a `name` attribute, it identifies a named format; if not, it identifies the default format.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

`name?`
: _eqname_
: A named format; if the attribute is omitted then the default format is used.

`decimal-separator?`
: _char_
: Specifies the character used to separate the integer part from the fractional part of the formatted number; the default is the period character (`.`).

`grouping-separator?`
: _char_
: Specifies the character typically used as a thousands separator; the default is the comma character (`,`).

`infinity?`
: _string_
: Specifies the string used to represent the `xs:double` value `INF`; the default is the string (`Infinity`).

`minus-sign?`
: _char_
: Specifies the character used to signal a negative number; the default is the hyphen-minus character (`-`).

`exponent-separator?`
: _char_
: Specifies the character used to separate the mantissa part from the exponent part of the formatted number; the default is the character (`e`). For use with XPath 3.1.

`NaN?`
: _string_
: Specifies the string used to represent the `xs:double` value `Nan` (not-a-number); the default is the string (`NaN`).

`percent?`
: _char_
: Specifies the character used to indicate that the number is represented as a per-hundred fraction; the default is the percent character (`%`).

`per-mille?`
: _char_
: Specifies the character used to indicate that the number is represented as a per-thousand fraction; the default is the Unicode per-mille character (`#x2030`).

`zero-digit?`
: _char_
: Specifies the character used to represent the digit zero; the default is the Western digit zero (`0`). Implicitly defines the characters used to represent each digit 0 to 9, as those in the corresponding Unicode decimal digit block.

`digit?`
: _char_
: Specifies the character used as a place-holder for an optional digit in the picture string; the default is the number sign character (`#`).

`pattern-separator?`
: _char_
: Specifies the character used to separate positive and negative sub-pictures in a picture string; the default is the semi-colon character (`;`).

## Details

In practice decimal formats are used only for formatting numbers using the `format-number()` function in XPath expressions.

With XSLT 3.0, the specification of `format-number()` has moved into XPath which means it is also available in XQuery. The `exponent-separator` attribute is new in XPath 3.1, and allows formating of numbers in scientific notation.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-decimal-format)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-decimal-format)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/decimal-format.html)

## See also

- [`xsl:number`](xsl-number.md)
