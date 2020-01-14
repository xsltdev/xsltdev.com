---
description: Invokes a named template
---

# xsl:call-template

Invokes a named template.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: [`xsl:with-param`](xsl-with-param.md)\*
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`name`**
: _eqname_
: Name of the called template, must match the name defined on an [`xsl:template`](xsl-template.md) element.

## Notes on the Saxon implementation

Until 9.6, Saxon supported an alternative instruction `saxon:call-template`, but this has now been dropped. This had the same effect as `xsl:call-template`, except that it allowed name attribute may be written as an attribute value template, allowing the called template to be decided at run-time. In place of this facility, XSLT 3.0 offers higher-order functions.

## Details

To supply parameters to the called template, one or more [`xsl:with-param`](xsl-with-param.md) elements may be included. The values of these parameters are available to the called template. If the `xsl:with-param` element specifies `tunnel="yes"`, then the parameter is passed transparently through to templates called at any depth, but it can only be referenced by an [`xsl:param`](xsl-param.md) element that also specifies `tunnel="yes"`. If the default value, `tunnel="no"` is used, then the parameter value is available only in the immediately called template, and only if the `xsl:param` element specifies `tunnel="no"` (explicitly or by defaulting the attribute).

The context of the called template (for example the current node and current node list) is the same as that for the calling template; however the variables defined in the calling template are not accessible in the called template.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-call-template)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-call-template)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/call-template.html)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:template`](xsl-template.md)
- [`xsl:with-param`](xsl-with-param.md)
