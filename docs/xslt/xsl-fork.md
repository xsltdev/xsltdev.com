---
description: The result of the xsl:fork instruction is the sequence formed by concatenating the results of evaluating each of its contained instructions, in order
---

# xsl:fork

The result of the **`xsl:fork`** instruction is the sequence formed by concatenating the results of evaluating each of its contained instructions, in order.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.7._

- **Category**: instruction
- **Content**: ( [`xsl:fallback`](xsl-fallback.md)\*, ( ( [`xsl:sequence`](xsl-sequence.md), [`xsl:fallback`](xsl-fallback.md)\* )\* | ( [`xsl:for-each-group`](xsl-for-each-group.md), [`xsl:fallback`](xsl-fallback.md)\* ) ) )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Notes on the Saxon implementation

The instruction is pointless when not streaming, but it is still supported.

Fully implemented since Saxon 9.7. Streaming of [`xsl:for-each-group`](xsl-for-each-group.md), as a child of `xsl:fork`, with a `group-by` attribute was introduced in 9.7 maintenance releases and is fully supported in Saxon 9.8.

In Saxon 9.6, the instruction was implemented with restrictions: specifically, the content of `xsl:fork` must consist of a sequence of [`xsl:sequence`](xsl-sequence.md) instructions, and can not include [`xsl:for-each-group`](xsl-for-each-group.md) elements.

The Saxon 9.6 implementation of [`xsl:fork`](xsl-fork.md) in streaming mode does not actually use multiple threads: rather, the events notified by the XML parser (such as startElement and endElement) are notified to each prong of the `xsl:fork` in turn. Each prong accumulates its result in a temporary tree held in memory, and these temporary trees are combined on completion. The instruction is most effective when each prong consists of a call to [`xsl:result-document`](xsl-result-document.md); in this case the output can immediately be serialized, leaving no temporary data in memory.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-fork)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/fork)

## See also

- [`xsl:fallback`](xsl-fallback.md)
