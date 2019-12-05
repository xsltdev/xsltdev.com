---
description: Used to iterate over a sequence, with the option to set parameters for use in the next iteration
---

# xsl:iterate

Used to iterate over a sequence, with the option to set parameters for use in the next iteration.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: instruction
- **Content**: ( [`xsl:param`](xsl-param.md)\* , [`xsl:on-completion`](xsl-on-completion.md)? , _sequence-constructor_ )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`select`**
: _expression_
: Input sequence over which the iteration is processed.

## Notes on the Saxon implementation

The ordering of elements within `xsl:iterate` has changed since the original W3C working draft ([`xsl:on-completion`](xsl-on-completion.md) now comes immediately after [`xsl:param`](xsl-param.md)). Since Saxon 9.7, only the new ordering is allowed. Saxon 9.6 allowed both the new and the old ordering, but gives a warning if the old ordering is used.

Earlier Saxon releases implemented a prototype of `xsl:iterate` as an extension in the Saxon namespace (`saxon:iterate`). This was dropped in Saxon 9.5.

For `xsl:iterate` to be streamable, the W3C rules require that the `select` expression must be "striding", which essentially means that it may use the child axis but not the descendant axis (to ensure that selected nodes do not overlap each other). Prior to Saxon 9.5, Saxon attempted to be more liberal than this, and allow limited streaming also when the descendant axis was used. Since Saxon 9.6, Saxon has been brought into line with the W3C specification. In many cases the restriction can be circumvented by using the outermost function, for example the expression `outermost(//title)` is striding even though it uses the descendant axis.

## Details

The `xsl:iterate` instruction is new in XSLT 3.0. It is similar to [`xsl:for-each`](xsl-for-each.md), except that the items in the input sequence are processed sequentially, and after processing each item in the input sequence it is possible to set parameters for use in the next iteration. It can therefore be used to solve problems that in XSLT 2.0 require recursive functions or templates.

The `xsl:iterate` instruction is motivated by use-cases for streaming, but it can also be used profitably in non-streaming situations. For more information see Streaming with `xsl:iterate`.

The instruction allows a child element [`xsl:on-completion`](xsl-on-completion.md) which defines processing to be carried out when the input sequence is exhausted. The instructions within `xsl:on-completion` have access to the final values of the parameters declared in the [`xsl:next-iteration`](xsl-next-iteration.md) instruction set while processing the last item in the sequence. An [`xsl:break`](xsl-break.md) element may be used within the enclosed sequence constructor of an `xsl:iterate` instruction, which causes premature completion before the entire input sequence has been processed.

## Examples

### Example 1

Computes the running balance of a sequence of financial transactions:

```xslt
<xsl:iterate select="transactions/transaction">
    <xsl:param name="balance" select="0.00" as="xs:decimal"/>
    <xsl:variable name="newBalance"
        select="$balance + xs:decimal(@value)"/>
    <balance date="{@date}" value="{$newBalance}"/>
    <xsl:next-iteration>
        <xsl:with-param name="balance" select="$newBalance"/>
    </xsl:next-iteration>
</xsl:iterate>
```

### Example 2

Copies the input sequence up to the first `<br>` element:

```xslt
<xsl:iterate select="*">
    <xsl:choose>
        <xsl:when test="self::br">
            <xsl:break/>
        </xsl:when>
        <xsl:otherwise>
            <xsl:copy-of select="."/>
        </xsl:otherwise>
    </xsl:choose>
</xsl:iterate>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-iterate)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/iterate)

## See also

- [`xsl:next-iteration`](xsl-next-iteration.md)
- [`xsl:break`](xsl-break.md)
- [`xsl:on-completion`](xsl-on-completion.md)
- [`xsl:for-each`](xsl-for-each.md)
