---
description: Used to declare a named collection of attributes, which will often be used together to define an output style
---

# xsl:attribute-set

Used to declare a named collection of attributes, which will often be used together to define an output style. It is declared at the top level (subordinate to [`xsl:stylesheet`](xsl-stylesheet.md)).

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: [`xsl:attribute`](xsl-attribute.md)\*
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-stylesheet.md); [`xsl:override`](xsl-override.md)

## Attributes

**`name`**
: _eqname_
: The name of the attribute set.

`use-attribute-sets?`
: _eqnames_
: Used to define this attribute set in terms of other named attribute sets, provided as a space-separated list.

`visibility?`
: `"public" | "private" | "final" | "abstract"`
: New in XSLT 3.0. Determines the potential visibility of the component corresponding to this attribute set; the default is `private`. All the declarations for an attribute set must have the same value for this attribute.

`streamable?`
: _boolean_
: New in XSLT 3.0. The value `yes` designates the attribute set as streamable. Requires Saxon-EE.

## Details

An attribute-set contains a collection of [`xsl:attribute`](xsl-attribute.md) elements.

The attributes in an attribute-set can be used in several ways:

- They can be added to a literal result element by specifying [`xsl:use-attribute-sets`](xsl-use-attribute-sets.md) in the list of attributes for the element. The value is a space-separated list of attribute-set names. Attributes specified explicitly on the literal result element, or added using [`xsl:attribute`](xsl-attribute.md), override any that are specified in the attribute-set definition.
- They can be added to an element created using [`xsl:element`](xsl-element.md), by specifying `use-attribute-sets` in the list of attributes for the `xsl:element` element. The value is a space-separated list of attribute-set names. Attributes specified explicitly on the literal result element, or added using `xsl:attribute`, override any that are specified in the attribute-set definition.
- One attribute set can be based on another by specifying `use-attribute-sets` in the list of attributes for the `xsl:attribute-set` element. Again, attributes defined explicitly in the attribute set override any that are included implicitly from another attribute set.

Attribute sets named in the `xsl:use-attribute-sets` or `use-attribute-sets` attribute are applied in the order given: if the same attribute is generated more than once, the later value always takes precedence.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-attribute-set)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-attribute-set)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/attribute-set.html)

## See also

- [`xsl:attribute`](xsl-attribute.md)
- [`xsl:element`](xsl-element.md)
