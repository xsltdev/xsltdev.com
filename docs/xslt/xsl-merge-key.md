---
description: Used to define the merge keys on which the input sequences of a merging operation are sorted
---

# xsl:merge-key

Used to define the merge keys on which the input sequences of a merging operation are sorted.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:merge-source`](xsl-merge-source.md)

## Attributes

`select?`
: _expression_
: The merge key can be defined either by a string expression in a select attribute, or by an enclosed sequence constructor.

`lang?`
: _{ language }_
: Declares the algorithm used for alphabetic collating, as an ISO language code such as `en` (English) or `de` (German). The default is based on the Java system locale.

`order?`
: `{ "ascending" | "descending" }`
: Declares the sort order; the default is `ascending`.

`collation?`
: _{ uri }_
: Declares the collation, by the name of a collating sequence.

`case-order?`
: `{ "upper-first" | "lower-first" }`
: Relevant only for `data-type="text"`; it declares whether uppercase letters are sorted before their lowercase equivalents, or vice-versa.

`data-type?`
: `{ "text" | "number" | eqname }`
: Declares whether collating is based on alphabetic sequence or numeric sequence. The permitted values are either `text` or `number`, or a built-in type in XML Schema, such as `xs:date` or `xs:decimal`.

## Details

The syntax and semantics of an `xsl:merge-key` element are closely based on the rules for the [`xsl:sort`](xsl-sort.md) element (the only exception being the absence of the `stable` attribute); the difference is that [`xsl:merge-key`](xsl-merge-key.md) elements do not cause a sort to take place, they merely declare the existing sort order of the input sequence.

For details and examples, see [`xsl:merge`](xsl-merge.md).

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-merge-key)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/merge-key)

## See also

- [`xsl:merge`](xsl-merge.md)
- [`xsl:merge-source`](xsl-merge-source.md)
