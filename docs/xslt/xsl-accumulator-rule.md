---
description: Defines a rule for an xsl accumulator
---

# xsl:accumulator-rule

Defines a rule for an [`xsl:accumulator`](xsl-accumulator.md).

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:accumulator`](xsl-accumulator.md)

## Attributes

**`match`**
: _pattern_
: Pattern defining the set of nodes to which the accumulator rule applies.

`phase?`
: `"start" | "end"`
: Determines whether the rule fires before or after descendants are processed, by specifying `phase="start"` (the default) or `phase="end"` respectively.

`select?`
: _expression_
: The expression to be evaluated by the rule may be given either by a select attribute, or by an enclosed sequence constructor.

`saxon:capture?`
: _boolean_
: The value `"yes|true|1"` on a `phase="end"` rule for a streaming accumulator removes the requirement for the select attribute (or sequence constructor) to be motionless. Instead the expression has access to a snapshot of the streamed node (in the sense of the `fn:snapshot` function). For example, writing `select="($value, .)"` ensures that the value of the accumulator contains a sequence of snapshot copies of all the element nodes matched by the accumulator rule. For details see `saxon:capture`.

## Examples

For an example of the use of a capturing accumulator rule to construct the glossary of a document, see the blog article [Capturing Accumulators](http://dev.saxonica.com/blog/mike/2018/03/capturing-accumulators.html).

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-accumulator-rule)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/accumulator-rule.html)

## See also

- [`xsl:accumulator`](xsl-accumulator.md)
