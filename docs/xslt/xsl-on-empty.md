---
description: Used to allow conditional content construction to be made streamable
---

# xsl:on-empty

Used to allow conditional content construction to be made streamable. Outputs the enclosed content only if the containing sequence generates no "ordinary" content.

If the instruction appears in a sequence constructor, it must come after all other instructions.

Although intended primarily to make streaming applications easier to write, the instruction can also be handy irrespective of streaming to avoid evaluating complex conditions more than once.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.7._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: _expression_

## Notes on the Saxon implementation

New in XSLT 3.0, and implemented since Saxon 9.7.

## Examples

The following code generates substitute text when there is no content, however it is not guaranteed-streamable because it processes child `item-for-sale` elements more than once:

```xslt
<xsl:apply-templates select="item-for-sale"/>
<xsl:if test="empty(item-for-sale)">
    <p>There are no items for sale.</p>
</xsl:if>
```

To make this streamable, it can be rewritten using the `xsl:on-empty` instruction:

```xslt
<xsl:sequence>
    <xsl:apply-templates select="item-for-sale"/>
    <xsl:on-empty>
        <p>There are no items for sale.</p>
    </xsl:on-empty>
</xsl:sequence>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-on-empty)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/on-empty.html)

## See also

- [`xsl:on-non-empty`](xsl-on-non-empty.md)
- [`xsl:where-populated`](xsl-where-populated.md)
