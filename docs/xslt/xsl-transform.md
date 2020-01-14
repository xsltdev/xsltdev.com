---
description: The name xsl transform is a synonym for xsl stylesheet
---

# xsl:transform

The name **`xsl:transform`** is a synonym for [`xsl:stylesheet`](xsl-stylesheet.md). This element is always the top-level element of an XSLT stylesheet.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Content**: ( _declarations_ )

## Attributes

`id?`
: _id_

**`version`**
: _decimal_

`default-mode?`
: `eqname | "#unnamed"`

`default-validation?`
: `"preserve" | "strip"`

`input-type-annotations?`
: `"preserve" | "strip" | "unspecified"`

`default-collation?`
: _uris_

`extension-element-prefixes?`
: _prefixes_

`exclude-result-prefixes?`
: _prefixes_

`expand-text?`
: _boolean_

`use-when?`
: _expression_

`xpath-default-namespace?`
: _uri_

## Details

See [`xsl:stylesheet`](xsl-stylesheet.md) for full details.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-transform)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-transform)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/transform.html)

## See also

- [`xsl:stylesheet`](xsl-stylesheet.md)
