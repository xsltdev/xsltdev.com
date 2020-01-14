---
description: An accumulator defines some processing that is to take place while a document is being sequentially processed
---

# xsl:accumulator

An accumulator defines some processing that is to take place while a document is being sequentially processed: for example, a total that is to be accumulated.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.5._

- **Category**: declaration
- **Content**: [`xsl:accumulator-rule`](xsl-accumulator-rule.md)+
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`name`**
: _eqname_
: Defines a name for the accumulator.

**`initial-value`**
: _expression_
: Defines the initial value of the accumulator.

`as?`
: _sequence-type_
: Defines the type of the accumulator variable; default is `item()*`.

`streamable?`
: _boolean_
: Requests streamed evaluation of the accumulator if set to yes. Requires Saxon-EE.

`saxon:trace?`
: `boolean`
: Causes a trace message to be output (to the Configuration's Logger) whenever the value of the accumulator changes. The message includes the name of the accumulator, the path of the node, and the new accumulator value. For details see `saxon:trace`.

## Notes on the Saxon implementation

Saxon-HE and -PE support a non-streaming implementation; Saxon-EE additionally supports a streaming implementation.

Saxon has two completely separate implementations, one for streamed documents and one for unstreamed documents. Accumulators are actively evaluated for every streamed document to which they are applicable, but for non-streamed documents, they are evaluated only on request (the first call of an accumulator function for a particular document triggers evaluation of the accumulator up to the node in question). The value of the accumulator for each non-streamed node is stored along with the node, using a data structure that allows for the fact that the accumulator value will often change only occasionally as you proceed through the document.

## Details

Accumulators are motivated by the need for streaming, but they can also be useful independently of streaming. The rationale is that when you are processing a document using streaming, you only get to see each node once, so it's quite likely that you need to remember what you have seen for use later. Accumulators provide this memory.

The idea of accumulators is to define some processing that is to take place while a document is being sequentially processed: for example, a total that is to be accumulated. The semantics are defined in terms of a traversal of the tree representing the document, with each node being visited once before traversing its subtree, and again after processing the subtree. On each visit (both the pre-descent visit and the post-descent visit) it is possible to define rules (using [`xsl:accumulator-rule`](xsl-accumulator-rule.md)) that are activated, whose effect is to compute a new value for the accumulator based on the previous value and the data visible at the node being processed. The expression used to compute the new value must be "motionless", that is, it must be computable without changing the current position of the streamed input.

Accumulators have a procedural feel to them, because the state of the accumulator is modified as the document is processed. Nevertheless, they are functionally "clean": the value of an accumulator at a particular node is a pure function of the node. Functional programming enthusiasts will recognize accumulators as being very similar to the "fold" operation that is often used to apply an operation to every item in a sequence, in turn.

An accumulator is accessible through two functions: the pre-descent function [`accumulator-before()`](../xpath/accumulator-before.md) and the post-descent function [`accumulator-after()`](../xpath/accumulator-after.md). These functions can be called supplying an accumulator as argument, to give the value of the accumulator for the context node before processing its children, and after processing its children. Sometimes the only value of interest is the post-descent value for the document node, that is, the value of the accumulator after the entire document has been processed.

Accumulators (unlike [`xsl:key`](xsl-key.md) elements) are applicable to some source documents and not others; the rules can be found at [Applicability of Accumulators](https://www.w3.org/TR/xslt-30/#applicability-of-accumulators).

## Examples

The XSLT 3.0 specification contains a number of [examples](http://www.w3.org/TR/xslt-30/#accumulator-examples) illustrating the use of accumulators, and studying these examples is probably the best way to gain an understanding of the feature.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-accumulator)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/accumulator.html)

## See also

- [`xsl:accumulator-rule`](xsl-accumulator-rule.md)
- [`accumulator-after()`](../xpath/accumulator-after.md)
- [`accumulator-before()`](../xpath/accumulator-before.md)
