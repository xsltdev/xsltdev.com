---
description: Used to declare the initial context item for a template whether the template requires a context item, and if so, what its expected type is
---

# xsl:context-item

Used to declare the initial context item for a template: whether the template requires a context item, and if so, what its expected type is.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.7._

- **Content**: none
- **Permitted parent elements**: [`xsl:template`](xsl-template.md)

## Attributes

`as?`
: _item-type_
: The required type of the context item; the default is `item()`.

`use?`
: `"required" | "optional" | "absent"`
: Specifies whether a template requires a context item; the default is `optional`.

## Notes on the Saxon implementation

Implemented since Saxon 9.7. The initial implementation is functionally complete, but the context item information is not used for optimization or for static type checking. The information is used for assessing streamability.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-context-item)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/context-item.html)
