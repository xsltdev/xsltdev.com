---
description: Used at the top level of the stylesheet to define elements in the source document for which whitespace nodes are insignificant and should be removed from the tree before processing
---

# xsl:strip-space

Used at the top level of the stylesheet to define elements in the source document for which whitespace nodes are insignificant and should be removed from the tree before processing.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`elements`**
: _tokens_
: Defines a space-separated list of element names. The value "`*`" may be used to mean "all elements"; in this case any elements where whitespace is not to be stripped may be indicated by an [`xsl:preserve-space`](xsl-preserve-space.md) element.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-strip-space)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-strip-space)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/strip-space.html)

## See also

- [`xsl:preserve-space`](xsl-preserve-space.md)
