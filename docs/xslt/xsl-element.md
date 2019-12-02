---
description: Used to create an output element whose name might be calculated at run-time
---

# xsl:element

Used to create an output element whose name might be calculated at run-time.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`name`**
: _{ qname }_
: The name of the generated element. The name attribute is an _attribute value_ template, so it may contain string expressions inside curly braces.

`namespace?`
: _{ uri }_
: The namespace URI of the element.

`inherit-namespaces?`
: _boolean_
: If the value is yes (the default), then the namespace nodes created for the generated element are copied to its children and descendants. If the value is no, then these namespace nodes are not automatically copied.

`use-attribute-sets?`
: _eqnames_
: Attributes of the generated element can be defined by reference to named attribute sets, provided as a whitespace-separated list. They are applied in the order given: if the same attribute is generated more than once, the later value always takes precedence.

`type?`
: _eqname_
: Added in XSLT 2.0. Indicates the data type of the value of the element. The value may be a built-in type defined in XML Schema, for example `xs:integer` or `xs:date`, or a user-defined type defined in a schema imported using [`xsl:import-schema`](xsl-import-schema.md). Type annotations are only accessible if the attribute is added to a temporary tree that specifies `type-information="preserve"`. The attribute causes the content of the element to be validated against the schema definition of the type, and will cause a fatal dynamic error if validation fails.

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`

## Notes on the Saxon implementation

When the element name is known at compile time, Saxon generates exactly the same code as for a literal result elements. Literal result elements are generally preferred in such cases because they are more readable.

Motivated by streaming, the on-empty attribute was introduced in an early Working Draft for XSLT 3.0, but later removed and replaced by the new [`xsl:on-empty`](xsl-on-empty.md), [`xsl:on-non-empty`](xsl-on-non-empty.md) and [`xsl:where-populated`](xsl-where-populated.md) instructions. The on-empty attribute was implemented in Saxon 9.5, but removed in 9.7.

## Details

The attributes of the generated element are defined by subsequent [`xsl:attribute`](xsl-attribute.md) elements, or by reference to named attribute sets using the optional `use-attribute-sets` attribute. The content of the generated element is whatever is generated between the `<xsl:element>` and `</xsl:element>` tags.

## Examples

The following code creates a `<FONT>` element with several attributes:

```xslt
<xsl:element name="FONT">
    <xsl:attribute name="SIZE">4</xsl:attribute>
    <xsl:attribute name="FACE">Courier New</xsl:attribute>
    Some output text
</xsl:element>
```

This example is equivalent to the simpler literal result element:

```html
<font size="4" face="Courier New">
  Some output text
</font>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-element)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-element)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/element)

## See also

- [`xsl:attribute`](xsl-attribute.md)
- [`xsl:copy`](xsl-copy.md)
