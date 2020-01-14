---
description: Used within an xsl merge instruction to define the processing to be carried out on each group of input items sharing a value for the merge key
---

# xsl:merge-action

Used within an [`xsl:merge`](xsl-merge.md) instruction to define the processing to be carried out on each group of input items sharing a value for the merge key.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:merge`](xsl-merge.md)
- **Element has no attributes**

## Notes on the Saxon implementation

In Saxon 9.6 the implementation of the [`current-merge-group()`](../xpath/fn-current-merge-group.md) function did not match the latest W3C specification. Instead of returning a map, it returned a sequence containing all items in the current merge group, regardless which merge source they came from.

Since Saxon 9.7, the implementation conforms with the final Recommendation.

## Details

For details and examples, see [`xsl:merge`](xsl-merge.md).

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-merge-action)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/merge-action.html)

## See also

- [`xsl:merge`](xsl-merge.md)
- [`current-merge-group()`](../xpath/fn-current-merge-group.md)
