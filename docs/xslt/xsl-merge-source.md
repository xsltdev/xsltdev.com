---
description: Describes the input source for an xsl merge instruction
---

# xsl:merge-source

Describes the input source for an [`xsl:merge`](xsl-merge.md) instruction.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Content**: [`xsl:merge-key`](xsl-merge-key.md)+
- **Permitted parent elements**: [`xsl:merge`](xsl-merge.md)

## Attributes

`name?`
: _ncname_
: Name of the merge source. Used to distinguish different merge sources within the [`xsl:merge-action`](xsl-merge-action.md) instructions.

`for-each-item?`
: _expression_
: XPath expression returning a set of nodes. Selects the anchor nodes for non-streamed merging.

`for-each-source?`
: _expression_
: XPath expression returning a set of URIs; these are the URIs of documents used for streamed merging; the root nodes of these documents act as the anchor nodes. In an earlier draft of the XSLT 3.0 specification, this attribute was named `for-each-stream`; either is accepted since Saxon 9.7.0.10.

**`select`**
: _expression_
: XPath expression; for each anchor node, this selects the descendant nodes that make up the stream of data to be merged.

`streamable?`
: _boolean_
: Streamed merging requires Saxon-EE.

`use-accumulators?`
: _tokens_
: First implemented in Saxon 9.8. Defines the set of accumulators that are applicable to the streamed document.

`sort-before-merge?`
: _boolean_
: Specifies whether each input sequence will first be sorted to ensure that it is in the correct order. The value yes means that sorting will take place, while the value no (the default) means that each input sequence must already be in the correct order for merging.

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`
: Determines whether validation is applied to the input read from this merge source. Validation requires Saxon-EE.

`type?`
: _eqname_
: If specified, data read from this merge source is validated against the named schema type. Validation requires Saxon-EE.

## Notes on the Saxon implementation

The implementation of streaming uses one thread for each input document. The configuration option to allow multi-threaded execution must not be disabled.

Streamed merging requires Saxon-EE.

The `use-accumulators` attribute is first implemented in Saxon 9.8.

## Details

For details and examples, see [`xsl:merge`](xsl-merge.md)

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-merge-source)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/merge-source)

## See also

- [`xsl:merge`](xsl-merge.md)
