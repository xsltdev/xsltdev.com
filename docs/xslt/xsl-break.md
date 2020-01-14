---
description: The xsl break instruction is used within xsl iterate, and causes premature completion before the entire input sequence has been processed
---

# xsl:break

The **`xsl:break`** instruction is used within [`xsl:iterate`](xsl-iterate.md), and causes premature completion before the entire input sequence has been processed. If there is a `select` attribute, or a contained sequence constructor, this is evaluated and added to the result of the containing [`xsl:iterate`](xsl-iterate.md) instruction.

The `xsl:break` instruction must not be followed by further instructions, though it can occur as the last thing in a branch of a conditional. It must appear lexically within the `xsl:iterate` instruction (and not, for example, in a called template or function).

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: _expression_
: The effect of the instruction may be defined either by a select attribute, or by an enclosed sequence constructor.

## Details

For details see [`xsl:iterate`](xsl-iterate.md).

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-break)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/break.html)

## See also

- [`xsl:iterate`](xsl-iterate.md)
