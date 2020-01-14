---
description: The xslattribute element is used to add an attribute value to an xslelement element or literal result element, or to an element created using xsl copy
---

# xsl:attribute

The **`xsl:attribute`** element is used to add an attribute value to an [`xsl:element`](xsl-element.md) element or literal result element, or to an element created using [`xsl:copy`](xsl-copy.md). The attribute must be output immediately after the element, with no intervening character data.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:attribute-set`](xsl-attribute-set.md); any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`name`**
: _{ qname }_
: Attribute name, interpreted as an attribute value template, so it may contain string expressions within curly braces. The full syntax of string expressions is outlined in XPath Expression Syntax.

`namespace?`
: _{ uri }_
: The namespace URI of the attribute.

`select?`
: _expression_
: The attribute value may be given either by a select attribute or by an enclosed sequence constructor. If the select attribute is used and the value is a sequence, then the items in the sequence are output space-separated.

`separator?`
: _{ string }_
: String used to specify an alternative separator.

`type?`
: _eqname_
: New in XSLT 2.0. Indicates the data type of the value of the attribute. The value must either be a built-in type defined in XML Schema, for example `xs:integer` or `xs:date`, or a user-defined type defined in a schema imported using [`xsl:import-schema`](xsl-import-schema.md). Type annotations are only accessible if the attribute is added to a temporary tree that specifies `validation="preserve"`. The value given to the attribute must be a string that conforms to the rules for the data type, as defined in XML Schema.

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`
: Invokes validation of the contents of the attribute.

## Notes on the Saxon implementation

Modivated by streaming, the on-empty attribute was introduced in an early Working Draft for XSLT 3.0, but later removed and replaced by the new [`xsl:on-empty`](xsl-on-empty.md), [`xsl:on-non-empty`](xsl-on-non-empty.md) and [`xsl:where-populated`](xsl-where-populated.md) instructions. The `on-empty` attribute was implemented in Saxon 9.5, but removed in 9.7.

## Details

There are two main uses for the `xsl:attribute` element:

- It is the only way to set attributes on an element generated dynamically using `xsl:element`.
- It allows attributes of a literal result element to be calculated using [`xsl:value-of`](xsl-value-of.md).

The `xsl:attribute` must be output immediately after the relevant element is generated: there must be no intervening character data (other than whitespace which is ignored). Saxon outputs the closing "`>`" of the element start tag as soon as something other than an attribute is written to the output stream, and rejects an attempt to output an attribute if there is no currently-open start tag. Any special characters within the attribute value will automatically be escaped (for example, "`<`" will be output as "`&lt;`").

If two attributes are output with the same name, the second one takes precedence.

## Examples

The following code creates a `<FONT>` element with several attributes:

```xslt
<xsl:element name="FONT">
    <xsl:attribute name="SIZE">4</xsl:attribute>
    <xsl:attribute name="FACE">Courier New</xsl:attribute>
    Some output text
</xsl:element>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-attribute)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-attribute)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/attribute.html)

## See also

- [`xsl:element`](xsl-element.md)
- [`xsl:copy`](xsl-copy.md)
