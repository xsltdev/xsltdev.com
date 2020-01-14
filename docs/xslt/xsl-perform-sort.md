---
description: Takes a sequence as its input and produces a sorted sequence as its output
---

# xsl:perform-sort

Takes a sequence as its input and produces a sorted sequence as its output.

_Available in XSLT 2.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: ( [`xsl:sort`](xsl-sort.md)+ , _sequence-constructor_ )
- **Permitted parent elements**: any XSLT element whose content model is sequence-constructor; any literal result element

## Attributes

`select?`
: expression
: The input sequence may be defined either by an expression within the optional `select` attribute, or by the enclosed sequence constructor.

## Details

The sort criteria are specified using [`xsl:sort`](xsl-sort.md) elements as children of `xsl:perform-sort`, in the usual way.

It's often useful to use `xsl:perform-sort` inside a stylesheet function; the function can return the sorted sequence as its result, and can be invoked directly from an XPath expression.

## Examples

```xslt
<xsl:perform-sort select="//BOOK">
    <xsl:sort select="author/last-name"/>
    <xsl:sort select="author/first-name"/>
</xsl:perform-sort>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-perform-sort)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-perform-sort)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/perform-sort)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:for-each`](xsl-for-each.md)
- [`xsl:sort`](xsl-sort.md)
