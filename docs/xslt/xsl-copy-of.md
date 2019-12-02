---
description: Copies the value obtained by evaluating the mandatory select attribute. It makes an exact copy
---

# xsl:copy-of

Copies the value obtained by evaluating the mandatory select attribute. It makes an exact copy.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: none
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`select`**
: _expression_
: Value to be copied (which may be any sequence of nodes, atomic values, and/or function items), given by an expression. If this expression is a string, a number, or a boolean, the effect is the same as using [`xsl:sequence`](xsl-sequence.md).

`copy-accumulators?`
: _boolean_
: New in XSLT 3.0. Used to copy the pre-descent and post-descent values of accumulators on source nodes to the new copies.

`copy-namespaces?`
: _boolean_
: Controls whether the in-scope namespaces of any element nodes copied by this instruction are automatically copied to the result. The default is yes. If the value is no, then namespaces will only be copied if they are actually used in the names of elements or attributes. This allows you, for example, to copy the contents of a SOAP message without copying the namespaces declared in its envelope.

`type?`
: _eqname_

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`

## Notes on the Saxon implementation

Earlier releases of Saxon supported an attribute `saxon:read-once` to control streaming behaviour. This is now superseded by the streaming features of XSLT 3.0; an error is reported if the attribute is used.

## Details

Making a deep copy of an element is particularly useful during streaming. For this reason XSLT 3.0 introduces an equivalent function, [`copy-of()`](../xpath/fn-copy-of.md). For example one can write `<xsl:for-each select="employee/copy-of()">` which processes a sequence of copies of the selected `<employee>` elements; the significance of using copies is that streaming constraints do not apply, since each `<employee>` element will be represented as a tree in memory, discarded as soon as that element has been processed.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-copy-of)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-copy-of)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/copy-of)

## See also

- [`xsl:copy`](xsl-copy.md)
- [`copy-of()`](../xpath/fn-copy-of.md)
