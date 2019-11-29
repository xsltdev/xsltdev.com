---
description: Searches for a template that matches the current node and that is defined in a stylesheet that was imported from the stylesheet containing the current template, and whose mode matches the current mode
---

# xsl:apply-imports

Searches for a template that matches the current node and that is defined in a stylesheet that was imported (directly or indirectly) from the stylesheet containing the current template, and whose mode matches the current mode. If there is such a template, it is activated using the current node. If not, the built-in template for the kind of node is activated.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: xsl:with-param\*
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Details

At run-time, there must be a current template. A current template is established when a template is activated as a result of a call on [`xsl:apply-templates`](xsl-apply-templates.md). Calling [`xsl:call-template`](xsl-call-template.md) does not change the current template. Calling [`xsl:for-each`](xsl-for-each.md) or [`xsl:for-each-group`](xsl-for-each-group.md) causes the current template to become null.

The `xsl:apply-imports` element is used in conjunction with imported stylesheets. The effect is to search for a template that matches the current node and that is defined in a stylesheet that was imported (directly or indirectly, possibly via [`xsl:include`](xsl-include.md)) from the stylesheet containing the current template, and whose mode matches the current mode. If there is such a template, it is activated using the current node. If not, the built-in template for the kind of node is activated.

To supply parameters to the called template, one or more [`xsl:with-param`](xsl-with-param.md) elements may be included. The values of these parameters are available to the called template. If the `xsl:with-param` element specifies `tunnel="yes"`, then the parameter is passed transparently through to templates called at any depth, but it can only be referenced by an [`xsl:param`](xsl-param.md) element that also specifies `tunnel="yes"`. If the default value, `tunnel="no"` is used, then the parameter value is available only in the immediately called template, and only if the `xsl:param` element specifies `tunnel="no"` (explicitly or by defaulting the attribute).

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-apply-imports)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-apply-imports)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/apply-imports)

## See also

- [`xsl:import`](xsl-import.md)
- [`xsl:next-match`](xsl-next-match.md)
- [`xsl:param`](xsl-param.md)
- [`xsl:with-param`](xsl-with-param.md)
