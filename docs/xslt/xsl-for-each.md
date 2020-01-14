---
description: Causes iteration over the nodes selected by a node-set expression
---

# xsl:for-each

Causes iteration over the nodes selected by a node-set expression.

Available in XSLT 1.0 and later versions. Available in all Saxon editions.

- **Category**: instruction
- **Content**: ( [`xsl:sort`](xsl-sort.md)\* , _sequence-constructor_ )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`select`**
: _expression_
: Defines the nodes over which the statement will iterate. The XSLT statements subordinate to the `xsl:for-each` element are applied to each source node selected by the node-set expression in turn. The full syntax of expressions is outlined in XPath Expression Syntax.

`saxon:threads?`
: _integer_
: The items selected by the `select` expression of the instruction are processed in parallel, using the specified number of threads. Requires Saxon-EE. For details see `saxon:threads`.

## Notes on the Saxon implementation

Saxon-EE offers an extension to the `xsl:for-each` instruction; the `saxon:threads` attribute allows the items in the input sequence to be processed in parallel. This is most likely to be effective when (a) the processing of each item is expensive, and (b) the output produced by processing each item is small. Allocating multiple threads when each item generates a new result document is pointless, because [`xsl:result-document`](xsl-result-document.md) already runs in a separate thread.

For `xsl:for-each` to be streamable, the W3C rules require that the `select` expression must be "striding", which essentially means that it may use the child axis but not the descendant axis (to ensure that selected nodes do not overlap each other). Prior to Saxon 9.5, Saxon attempted to be more liberal than this, and allow limited streaming also when the descendant axis was used. Since Saxon 9.6, the implementation has been brought into line with the W3C specification. In many cases the restriction can be circumvented by using the `outermost` function, for example the expression `outermost(//title)` is striding even though it uses the descendant axis.

## Details

The `xsl:for-each` element can be used as an alternative to [`xsl:apply-templates`](xsl-apply-templates.md) where the child nodes of the current node are known in advance.

It may have one or more [`xsl:sort`](xsl-sort.md) child elements to define the order of sorting. The sort keys are specified in major-to-minor order. The expression used for sorting can be any string expression. The following are particularly useful:

- element-name, e.g. `TITLE`: sorts on the value of a child element
- attribute-name, e.g. `@CODE`: sorts on the value of an attribute
- "`.`": sorts on the character content of the element
- "`qname(.)`": sorts on the name of the element

## Examples

### Example 1

```xslt
<xsl:template match="BOOKLIST">
    <TABLE>
    <xsl:for-each select="BOOK">
        <TR>
        <TD><xsl:value-of select="TITLE"/></TD>
        <TD><xsl:value-of select="AUTHOR"/></TD>
        <TD><xsl:value-of select="ISBN"/></TD>
        </TR>
    </xsl:for-each>
    </TABLE>
</xsl:template>
```

### Example 2

Sorting with `xsl:for-each`. This example shows a template for a `<BOOKLIST>` element which processes all the child `<BOOK>` elements in order of their child `<AUTHOR>` elements.

```xslt
<xsl:template match="BOOKLIST">
    <h2>
        <xsl:for-each select="BOOK">
            <xsl:sort select="AUTHOR"/>
            <p>AUTHOR: <xsl:value-of select="AUTHOR"/></p>
            <p>TITLE: <xsl:value-of select="TITLE"/></p>
            <hr/>
        </xsl:for-each>
    </h2>
</xsl:template>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-for-each)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-for-each)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/for-each.html)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:sort`](xsl-sort.md)
