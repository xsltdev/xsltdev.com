---
description: Causes an XML processing instruction to be output
---

# xsl:processing-instruction

Causes an XML processing instruction to be output.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`name`**
: _{ ncname }_
: The name of the PI. This attribute is interpreted as an _attribute value template_, so it may contain string expressions within curly braces.

`select?`
: _expression_
: The data part of the PI may be given either by a `select` attribute or by an enclosed sequence constructor. If the `select` attribute is used and the value is a sequence, then the items in the sequence are output space-separated.

## Details

The `xsl:processing-instruction` element can appear anywhere within an [`xsl:template`](xsl-template.md). Note that special characters occurring within the PI text will `not` be escaped.

## Examples

```xslt
<xsl:processing-instruction name="submit-invoice">version="1.0"</xsl:processing-instruction>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-processing-instruction)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-processing-instruction)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/processing-instruction)
