---
title: when
description: xsl when - Used within an xsl choose element to indicate one of a number of choices
---

# xsl:when

Used within an xsl:choose element to indicate one of a number of choices.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:choose`](xsl-choose.md)

## Attributes

**`test`**
: _expression_
: Match pattern. If this is the first `xsl:when` element within the enclosing [`xsl:choose`](xsl-choose.md) whose test condition matches the current element, the content of the `xsl:when` element is expanded, otherwise it is ignored.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-when)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-when)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/when.html)

## See also

- [`xsl:choose`](xsl-choose.md)
- [`xsl:otherwise`](xsl-otherwise.md)
- [`xsl:if`](xsl-if.md)
