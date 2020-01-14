---
description: Causes its content to be output
---

# xsl:text

Causes its content to be output. The main reason for enclosing text within an `xsl:text` element is to allow whitespace to be output. Whitespace nodes in the stylesheet are ignored unless they appear immediately within an `xsl:text` element.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: `#PCDATA`
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`[disable-output-escaping]?`
: _boolean_
: If set to yes, special characters such as "`<`" and "`&`" will be output as themselves, not as entities. Be aware that in general this can produce non-well-formed XML or HTML. It is useful, however, when generating things such as ASP or JSP pages. Escaping may not be disabled when writing to a result tree fragment. The default is no.

## Details

In XSLT 3.0, note that generally text value templates (expressions within curly braces) are NOT recognized within `xsl:text`. However the standard attribute `expand-text` can be used to enable their use. Text value templates can be used within an `xsl:text` element if the nearest ancestor which has an `expand-text` attribute has the value yes for this attribute. (See [`xsl:stylesheet`](xsl-stylesheet.md) for details on the standard attribute `expand-text`.)

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-text)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-text)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/text.html)

## See also

- [`xsl:character-map`](xsl-character-map.md)
- [`xsl:value-of`](xsl-value-of.md)
