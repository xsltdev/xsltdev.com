---
description: Used to define recovery action to be taken when an instruction element is used in the stylesheet and no implementation of that element is available
---

# xsl:fallback

Used to define recovery action to be taken when an instruction element is used in the stylesheet and no implementation of that element is available.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:analyze-string`](xsl-analyze-string.md); [`xsl:evaluate`](xsl-evaluate.md); [`xsl:fork`](xsl-fork.md); [`xsl:merge`](xsl-merge.md); [`xsl:next-match`](xsl-next-match.md); [`xsl:try`](xsl-try.md); any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Details

The `xsl:fallback` element is used when a stylesheet contains an instruction element and no implementation of that element is available. An element is an instruction element if its namespace URI is the standard URI for XSLT elements or if its namespace is identified in the `extension-element-prefixes` attribute of a containing literal result element, or in the `extension-element-prefixes` attribute of the [`xsl:stylesheet`](xsl-stylesheet.md) element.

If the `xsl:fallback` element appears in any other context, it is ignored, together with all its child and descendant elements.

If the parent element can be instantiated and processed, the `xsl:fallback` element and its descendants are ignored. If the parent element is not recognised or if any failure occurs instantiating it, all its `xsl:fallback` children are processed in turn. If there are no `xsl:fallback` children, an error is reported.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-fallback)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-fallback)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/fallback.html)
