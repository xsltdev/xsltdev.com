---
description: The purpose of the instruction is to allow merging of two or more pre-sorted input files, optionally using streamed processing of any or all of the inputs
---

# xsl:merge

The purpose of the instruction is to allow merging of two or more pre-sorted input files, optionally using streamed processing of any or all of the inputs.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.4._

- **Category**: instruction
- **Content**: ( [`xsl:merge-source`](xsl-merge-source.md)+, [`xsl:merge-action`](xsl-merge-action.md), [`xsl:fallback`](xsl-fallback.md)\* )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Notes on the Saxon implementation

The `xsl:merge` instruction is new in XSLT 3.0, and was first implemented in Saxon-EE 9.4. There have been a number of changes to the specification in successive working drafts; since Saxon 9.8, the implementation conforms with the final XSLT 3.0 Recommendation.

Saxon 9.5 implemented the `sort-before-merge` attribute, which allows the input to be sorted before merging.

Saxon 9.6 introduced support for streamed merging. There was one departure from the specification: the nodes selected for merging using the `xsl:merge-source/@select` are copies of the nodes in the source document (in the sense of the `copy-of()` function), rather than snapshots (as defined by the `snapshot()` function). This means that ancestors of the selected nodes, and attributes of ancestors, are not available.

Streamed processing requires Saxon-EE, but the instruction is implemented without streaming in Saxon-PE and Saxon-HE.

## Details

Each kind of input source is described in an [`xsl:merge-source`](xsl-merge-source.md) child element of the `xsl:merge` instruction; if there are multiple instances of that kind of input source, they are selected in the `for-each-item` or `for-each-source` attribute of the [`xsl:merge-source`](xsl-merge-source.md) element, while the `select` attribute selects the actual nodes forming the input sequence. The processing to be carried out on each group of input items sharing a value for the merge key is defined in an [`xsl:merge-action`](xsl-merge-action.md) element.

## Examples

### Example 1

Merges a homogenous collection of log files, each already sorted by timestamp:

```xslt
<xsl:merge>
    <xsl:merge-source for-each-item="collection('log-collection')" select="events/event"/>
        <xsl:merge-key select="@timestamp" order="ascending"/>
    </xsl:merge-source>
    <xsl:merge-action>
        <xsl:sequence select="current-merge-group()"/>
    </xsl:merge-action>
</xsl:merge>
```

### Example 2

Merges two log files with different internal structure:

```xslt
<xsl:merge>
    <xsl:merge-source select="doc('log1.xml')/transactions/transaction"/>
        <xsl:merge-key select="xs:dateTime(@date, @time)" order="ascending"/>
    </xsl:merge-source>
    <xsl:merge-source select="doc('log2.xml')/eventdata/transfer"/>
        <xsl:merge-key select="@timestamp" order="ascending"/>
    </xsl:merge-source>
    <xsl:merge-action>
        <xsl:apply-templates select="current-merge-group()"/>
    </xsl:merge-action>
</xsl:merge>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-merge)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/merge)

## See also

- [`xsl:merge-action`](xsl-merge-action.md)
- [`xsl:merge-source`](xsl-merge-source.md)
