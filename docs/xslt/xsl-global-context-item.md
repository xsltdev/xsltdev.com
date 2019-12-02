---
description: Used to declare whether a global context item is required, and if so, to declare its required type
---

# xsl:global-context-item

Used to declare whether a global context item is required, and if so, to declare its required type.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Requires Saxon-PE or Saxon-EE. Implemented since Saxon 9.7._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

`as?`
: _item-type_
: The required type of the global context item; the default is `item()`.

`use?`
: `"required" | "optional" | "absent"`
: Specifies whether a stylesheet module requires a global context item; the default is `optional`.

## Notes on the Saxon implementation

Implemented since Saxon 9.7.

An earlier draft of the XSLT 3.0 specification defined attributes `streamable` and `use-accumulators` (to define which accumulators are available with the document containing the global context item) for `xsl:global-context-item`. These were briefly implemented in Saxon but have now been dropped.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-global-context-item)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/global-context-item)
