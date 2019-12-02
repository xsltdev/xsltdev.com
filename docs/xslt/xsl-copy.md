---
description: Causes the current XML node in the source document to be copied to the output
---

# xsl:copy

Causes the current XML node in the source document to be copied to the output. The actual effect depends on whether the node is an element, an attribute, or a text node.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: _expression_
: New in XSLT 3.0. Allows a node other than the context node to be copied. This is useful when the instruction appears inside [`xsl:function`](xsl-function.md).

`copy-namespaces?`
: _boolean_
: Used only when copying element nodes. If the value is `yes` (the default), then all namespace nodes of the source element are copied as namespace nodes for the newly constructed element. If the value is `no`, then the namespace nodes are not copied.

`inherit-namespaces?`
: _boolean_
: Used only when copying element nodes. If the value is `yes` (the default), then the namespace nodes created for the newly constructed element are copied to its children and descendants. If the value is `no`, then these namespace nodes are not automatically copied.

`use-attribute-sets?`
: _eqnames_
: Used only when copying element nodes. Attributes of a generated element can be defined by reference to named attribute sets, provided as a whitespace-separated list. They are applied in the order given: if the same attribute is generated more than once, the later value always takes precedence.

`type?`
: _eqname_

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`

## Notes on the Saxon implementation

Modivated by streaming, the on-empty attribute was introduced in an early Working Draft for XSLT 3.0, but later removed and replaced by the new [`xsl:on-empty`](xsl-on-empty.md), [`xsl:on-non-empty`](xsl-on-non-empty.md) and [`xsl:where-populated`](xsl-where-populated.md) instructions. The `on-empty` attribute was implemented in Saxon 9.5, but removed in 9.7.

## Details

When `xsl:copy` is applied to an element node, the start and end element tags are copied; the attributes, character content and child elements are copied only if [`xsl:apply-templates`](xsl-apply-templates.md) is used within [`xsl:copy`](xsl-copy.md).

## Examples

A template that copies the input element to the output, together with all its child elements, character content, and attributes:

```xslt
<xsl:template match="*|text()|@*">
    <xsl:copy>
        <xsl:apply-templates select="@*"/>
        <xsl:apply-templates/>
    </xsl:copy>
</xsl:template>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-copy)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-copy)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/copy)

## See also

- [`xsl:copy-of`](xsl-copy-of.md)
