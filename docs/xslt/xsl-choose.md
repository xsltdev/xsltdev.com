---
description: Used to choose one of a number of alternative outputs
---

# xsl:choose

Used to choose one of a number of alternative outputs.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: ( [`xsl:when`](xsl-when.md)+ , [`xsl:otherwise`](xsl-otherwise.md)? )
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Notes on the Saxon implementation

Saxon-EE optimizes an `xsl:choose` instruction whose conditions are all of the form EXP = `value` where the left-hand expression is the same expression in each case, and the value is a literal (typically different in each case). The optimized form is similar to an XQuery `switch` expression: The expression EXP is only evaluated once, and a hash table is used to decide which branch to execute. Slight variants on this form of condition are also recognized, for example multiple such conditions connected by `"or"`, or use of the operator `"eq"` in place of `"="`.

If the result of the `xsl:choose` instruction is required to be a particular type, the type checking is moved into each branch; this means that for any branch where the type can be verified statically, no dynamic check is needed. This also means that if there is any branch whose static type is incompatible with the required type, a compile-time error will be reported even if the branch is never executed.

## Details

The element typically contains a number of [`xsl:when`](xsl-when.md) elements, each with a separate test condition. The first `xsl:when` element whose condition matches the current element in the source document is expanded, the others are ignored. If none of the conditions is satisfied, the [`xsl:otherwise`](xsl-otherwise.md) child element, if any, is expanded.

The test condition in the `xsl:when` element is a boolean expression. The full syntax of expressions is outlined in XPath Expression Syntax.

## Examples

```xslt
<xsl:choose>
    <xsl:when test="@cat='F'">Fiction</xsl:when>
    <xsl:when test="@cat='C'">Crime</xsl:when>
    <xsl:when test="@cat='R'">Reference</xsl:when>
    <xsl:otherwise>General</xsl:otherwise>
</xsl:choose>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-choose)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-choose)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/choose)

## See also

- [`xsl:when`](xsl-when.md)
- [`xsl:otherwise`](xsl-otherwise.md)
- [`xsl:if`](xsl-if.md)
