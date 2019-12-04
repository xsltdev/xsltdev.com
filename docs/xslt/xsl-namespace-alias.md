---
description: A top-level element used to control the mapping between a namespace URI used in the stylesheet and the corresponding namespace URI used in the result document
---

# xsl:namespace-alias

A top-level element used to control the mapping between a namespace URI used in the stylesheet and the corresponding namespace URI used in the result document.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`stylesheet-prefix`**
: _prefix_ | `"#default"`
: The namespace prefix used in the stylesheet.

**`result-prefix`**
: _prefix_ | `"#default"`
: The namespace prefix used in the result document.

## Details

Normally when a literal result element is encountered in a template, the namespace used for the element name and attribute names in the result document is the same as the namespace used in the stylesheet. If a different namespace is wanted (e.g. because the result document is a stylesheet using the XSLT namespace), then `xsl:namespace-alias` can be used to define the mapping.

## Examples

The following example allows the prefix `outxsl` to be used for output elements that are to be associated with the XSLT namespace. It assumes that both namespaces `xsl` and `outxsl` have been declared and are in scope.

```xslt
<xsl:namespace-alias stylesheet-prefix="outxsl" result-prefix="xsl"/>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-namespace-alias)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-namespace-alias)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/namespace-alias)
