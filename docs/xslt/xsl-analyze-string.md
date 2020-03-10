---
description: Applies a regular expression to a supplied string value
---

# xsl:analyze-string

Applies a regular expression to a supplied string value.

_Available in XSLT 2.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: ( [`xsl:matching-substring`](xsl-matching-substring.md)?, [`xsl:non-matching-substring`](xsl-non-matching-substring.md)?, [`xsl:fallback`](xsl-fallback.md)\* )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`select`**
: _expression_
: XPath expression whose value is the string to be analyzed.

**`regex`**
: _{ string }_
: The regular expression, which may be given as an attribute value template.

`flags?`
: _{ string }_
: One or more Perl-like flags to control the way in which regular expression matching is performed, for example the value m indicates multi-line mode.

## Notes on the Saxon implementation

XSLT 3.0 removes the restriction that the regular expression must not be one that matches a zero-length string, so this is now allowed since Saxon 9.6.

Saxon allows the flags attribute to contain "`;j`" or "`;n`" at the end, to indicate that the Java or .NET regular expression engine should be used in preference to Saxon's own regular expression engine. When this option is used, the rules for regular expressions will be the rules from Java or .NET, rather than the XPath-defined rules.

## Details

The `xsl:analyze-string` element applies a regular expression to a supplied string value. The string is split into a sequence of substrings, each of which is classified as either a matching substring (if it matches the regular expression) or a non-matching substring (if it doesn't). The substrings are then processed individually: the matching substrings by a [`xsl:matching-substring`](xsl-matching-substring.md) element that appears as a child of the `xsl:analyze-string` instruction, the non-matching substrings by a similar [`xsl:non-matching-substring`](xsl-non-matching-substring.md) element. If either of these is omitted, the relevant substrings are not processed.

When processing matching substrings, it is possible to call the `regex-group()` function to find the parts of the matching substring that matched particular parenthesized groups within the regular expression.

## Examples

[Examples](http://www.w3.org/TR/xslt-30/#regex-examples) of this element can be found in the XSLT 3.0 Specification.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-analyze-string)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-analyze-string)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/analyze-string.html)

## See also

- [`xsl:matching-substring`](xsl-matching-substring.md)
- [`xsl:non-matching-substring`](xsl-non-matching-substring.md)
