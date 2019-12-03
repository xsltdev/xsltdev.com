---
description: Used to construct a singleton map (one key and one value)
---

# xsl:map-entry

Used to construct a singleton map (one key and one value).

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`key`**
: _expression_
: Expression which defines the key of the entry in the new map.

`select?`
: _expression_
: The associated value can be defined either by a `select` attribute or by an enclosed sequence constructor.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-map-entry)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/map-entry)

## See also

- [`xsl:map`](xsl-map.md)
