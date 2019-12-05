---
description: Selects a sequence of nodes and/or atomic values and organizes them into subsets called groups
---

# xsl:for-each-group

Selects a sequence of nodes and/or atomic values and organizes them into subsets called groups.

_Available in XSLT 2.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: ( [`xsl:sort`](xsl-sort.md)\* , _sequence-constructor_ )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`select`**
: _expression_
: Expression to select nodes/values.

`group-by?`
: _expression_
: Groups together all items having the same value for a grouping key. The grouping key may have multiple values (a sequence of values) in which case the item is added to more than one group.

`group-adjacent?`
: _expression_
: Groups together all items having the same value for a grouping key, provided that they are also adjacent in the input sequence. This is useful when you need to wrap a new element around a sequence of related elements in the source documents, for example a consecutive sequence of `<bullet>` elements. In this case the grouping key must be single-valued.

`group-starting-with?`
: _pattern_
: Processes the items in the supplied sequence in turn, starting a new group whenever one of the items matches a specified pattern. This is useful, for example, when matching an `<h2>` element and its following `<p>` elements.

`group-ending-with?`
: _pattern_
: Processes the items in the supplied sequence in turn, closing the current group whenever one of the items matches a specified pattern. This is useful when matching a sequence of items in which the last item in the group carries some distinguishing attribute such as `continued="no"`.

`composite?`
: _boolean_
: Can be used when grouping using either `group-by` or `group-adjacent`. If set to `yes`, then the `group-by` and `group-adjacent` expressions may evaluate to a sequence, and grouping is done by comparing the entire sequence. If set to no (the default), then when `group-by` evaluates to a sequence, the relevant item has multiple grouping keys and goes in multiple groups; with `group-adjacent`, a sequence-valued grouping key is then an error.

`collation?`
: _{ uri }_
: The name of a collating sequence, used when comparing grouping keys. Can be used when grouping using either `group-by` or `group-adjacent`. If present it must be a collation URI that uses the scheme and path `http://www.w3.org/2013/collation/UCA`, in which case it requests use of the Unicode Collation Algorithm, or is a collation otherwise recognized by Saxon: see Collation.

## Notes on the Saxon implementation

Earlier drafts of XSLT 3.0 introduced new attributes `bind-group` and `bind-grouping-key`; these are no longer supported since Saxon 9.6.

The `composite` attribute has been implemented since Saxon 9.6.

Since 9.6, Saxon supports streamed grouping when the `group-adjacent`, `group-starting-with`, or `group-ending-with` attributes are used. Streaming with a `group-by` attribute became available in 9.7 maintenance releases and is fully supported in Saxon 9.8 (in this case the `xsl:for-each-group` instruction must appear within [`xsl:fork`](xsl-fork.md).)

## Details

There are four possible ways of defining the grouping using different attributes: `group-by`, `group-adjacent`, `group-starting-with`, and `group-ending-with`.

In XSLT 3.0, the capabilities of the `xsl:for-each-group` instruction are extended by virtue of the fact that the pattern used in `group-starting-with` or `group-ending-with` can now match atomic values as well as nodes.

## Examples

For examples of using the instruction, see the [XSLT 2.0 specification](http://www.w3.org/TR/xslt20/#grouping).

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-for-each-group)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-for-each-group)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/for-each-group)

## See also

- [`xsl:sort`](xsl-sort.md)
- [`current-group()`](../xpath/fn-current-group.md)
- [`current-grouping-key()`](../xpath/fn-current-grouping-key.md)
