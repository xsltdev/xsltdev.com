---
description: Used for conditional processing
---

# xsl:if

Used for conditional processing. It takes a mandatory test attribute, whose value is a boolean expression. The contents of the `xsl:if` element are expanded only of the expression is true.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`test`**
: _expression_
: The boolean expression to be tested. The full syntax of boolean expressions is outlined in XPath Expression Syntax.

## Examples

Includes a hyperlink in the output only if the current element has a preface attribute:

```xslt
<xsl:if test="@preface">
    <a href="preface.html">Preface</a>
</xsl:if>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-if)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-if)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/if)

## See also

- [`xsl:choose`](xsl-choose.md)
