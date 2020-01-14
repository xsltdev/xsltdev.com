---
description: Used within an xsl for-each, xsl apply-templates, xsl for-each-group, or xsl perform-sort to indicate the order in which the selected elements are processed
---

# xsl:sort

Used within an [`xsl:for-each`](xsl-for-each.md), [`xsl:apply-templates`](xsl-apply-templates.md), [`xsl:for-each-group`](xsl-for-each-group.md), or [`xsl:perform-sort`](xsl-perform-sort.md) to indicate the order in which the selected elements are processed.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:apply-templates`](xsl-apply-templates.md); [`xsl:for-each`](xsl-for-each.md); [`xsl:for-each-group`](xsl-for-each-group.md); [`xsl:perform-sort`](xsl-perform-sort.md)

## Attributes

`select?`
: _expression_
: A string expression that calculates the sort key. Default value "`.`".

`lang?`
: _{ language }_
: Determines the algorithm used for alphabetic collating, as an ISO language code such as `en` (English) or `de` (German). The default is based on the Java system locale. The value is used to select a collating sequence associated with the Java Locale for that language.

`order?`
: `{ "ascending" | "descending" }`
: Determines the sort order; the default is `ascending`. There is no control over language, collating sequence, or data type.

`collation?`
: _{ uri }_
: The name of a collating sequence. If present it must be a collation URI recognized by Saxon.

`stable?`
: _{ boolean }_
: Permitted only on the first `xsl:sort` element within a sort key. Determines the ordering when two sort key values compare equal. For such elements, the value `yes` (the default) means that the order after sorting is the same as the order before sorting; while the value `no` means that the ordering is implementation-dependent.

`case-order?`
: `{ "upper-first" | "lower-first" }`
: Relevant only for `data-type="text"`; it determines whether uppercase letters are sorted before their lowercase equivalents, or vice-versa.

`data-type?`
: `{ "text" | "number" | eqname }`
: Determines whether collating is based on alphabetic sequence or numeric sequence. The permitted values are either `text` or `number`, or a built-in type in XML Schema, such as `xs:date` or `xs:decimal`.

## Notes on the Saxon implementation

The Saxon implementation uses an internal sort routine using the QuickSort algorithm.

## Details

When using the Unicode Collation Algorithm, only the order and `data-type` control attributes are relevant - all other controls are attached as query parameters to the collation URI.

Several sort keys are allowed: they are written in major-to-minor order.

## Examples

### Example 1

Sorting with `xsl:apply-templates`. This example shows a template for a `<BOOKLIST>` element which processes all the child `<BOOK>` elements in order of their child `<AUTHOR>` elements; books with the same author are in descending order of the `DATE` attribute.

```xslt
<xsl:template match="BOOKLIST">
    <h2>
        <xsl:apply-templates select="BOOK">
            <xsl:sort select="AUTHOR"/>
            <xsl:sort select="@DATE" order="descending" lang="GregorianDate"/>
        </xsl:apply-templates>
    </h2>
</xsl:template>
```

### Example 2

Sorting with `xsl:for-each`. This example also shows a template for a `<BOOKLIST>` element which processes all the child `<BOOK>` elements in order of their child `<AUTHOR>` elements.

```xslt
<xsl:template match="BOOKLIST">
    <h2>
        <xsl:for-each select="BOOK">
            <xsl:sort select="AUTHOR"/>
            <p>AUTHOR: <xsl:value-of select="AUTHOR"></p>
            <p>TITLE: <xsl:value-of select="TITLE"></p>
            <hr/>
        </xsl:for-each>
    </h2>
</xsl:template>
```

### Example 3

Sorting with `xsl:for-each` using Unicode Collation Algorithm. `<BOOK>` elements are processed in order of their child `<TITLE>` elements, sorted as if they were in French dictionary order (where accents are compared in a reverse direction).

```xslt
<xsl:for-each select="BOOK">
    <xsl:sort select="TITLE"
         collation="http://www.w3.org/2013/collation/UCA?lang=fr;strength=tertiary;backwards=yes"/>
    <p>AUTHOR: <xsl:value-of select="AUTHOR"></p>
    <p>TITLE: <xsl:value-of select="TITLE"></p>
    <hr/>
</xsl:for-each>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-sort)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-sort)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/sort)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:for-each`](xsl-for-each.md)
- [`xsl:for-each-group`](xsl-for-each-group.md)
- [`xsl:perform-sort`](xsl-perform-sort.md)
