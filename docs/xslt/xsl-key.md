---
description: Used at the top level of the stylesheet to declare an attribute, or other value, that may be used as a key to identify nodes using the key() function within an expression
---

# xsl:key

Used at the top level of the stylesheet to declare an attribute, or other value, that may be used as a key to identify nodes using the `key()` function within an expression. Each `xsl:key` definition declares a named key, which must match the name of the key used in the `key()` function.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`name`**
: _eqname_
: Name of the key.

**`match`**
: _pattern_
: Pattern defining the set of nodes to which the key applies. For example, if `match="ACT|SCENE"` then every `<ACT>` element and every `<SCENE>` element is indexed by this key.

`use?`
: _expression_
: Expression to determine the value of the key, evaluated for each matched element. If the expression returns a node-set, the typed value of each node in this node-set acts as a key value. For example, if `use="AUTHOR"`, then each `<AUTHOR>` child of the matched element supplies one key value. The value of the key may alternatively be specified by the enclosed sequence constructor.

`composite?`
: _boolean_
: Implemented since Saxon 9.7. If the key specifier returns a sequence of atomic values, then this attribute determines whether each value is treated as an individual key (when `composite="no"`, the default), or the sequence is treated as a composite key (when `composite="yes"`).

`collation?`
: _uri_
: The name of a collating sequence, used when comparing strings. If present it must be a collation URI recognized by Saxon.

## Notes on the Saxon implementation

A key declaration does not apply to any particular source document; in principle, it applies to every document. Saxon builds an index for a particular document the first time the `key()` function is used to search that document. The Saxon implementation goes to some lengths to ensure that when the same stylesheet is applied repeatedly to the same source document (perhaps a lookup document used in many transformations), the key is only built once. The memory used by a key is freed as soon as either the source document or the stylesheet are garbage-collected.

The ability to define composite keys is new in XSLT 3.0 and is implemented since Saxon 9.7. (In Saxon 9.6, using the attribute `composite="yes"` generated an error.)

The Saxon-EE optimizer will automatically create additional keys where these appear to be useful.

Saxon provides an extension function `saxon:key-map()` which returns a map giving access to the index constructed using `xsl:key`.

## Details

Note that:

1. Keys are not unique: the same value may identify many different nodes
2. Keys are multi-valued: each matched node may have several (zero or more) values of the key, any one of which may be used to locate that node
3. Keys can only be used to identify nodes within a single XML document: the `key()` function will return nodes that are in the same document as the current node.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-key)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-key)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/key.html)

## See also

- [`key()`](../xpath/fn-key.md)
