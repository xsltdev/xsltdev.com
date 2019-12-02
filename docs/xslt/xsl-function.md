---
description: Defines a function within a stylesheet
---

# xsl:function

Defines a function within a stylesheet. The function is written in XSLT but it may be called from any XPath expression in the stylesheet. It must have a non-default namespace prefix.

_Available in XSLT 2.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: ( [`xsl:param`](xsl-param.md)* , *sequence-constructor\* )
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md); [`xsl:override`](xsl-override.md)

## Attributes

`name`
: _eqname_
: Name of the function. Must be in a non-default namespace.

`as?`
: _sequence-type_
: Defines the return type of the function.

`visibility?`
: `"public" | "private" | "final" | "abstract"`
: New in XSLT 3.0. Determines the visibility of the function in other packages.

`streamability?`
: `"unclassified" | "absorbing" | "inspection" | "filter" | "shallow-descent" | "deep-descent" | "ascent" | eqname`
: Not implemented in Saxon 9.7.

`override-extension-function?`
: _boolean_
: Determines what happens if this function has the same name and arity as another provided by the implementation or made available in the static context by an implementation-defined mechanism. If the value is yes (the default), then this function takes precedence; if the value is no, then the other function takes precedence.

`[override]?`
: _boolean_
: A deprecated synonym of `override-extension-function`, retained for XSLT 2.0 compatibility.

`new-each-time?`
: `"yes" | "true" | "1" | "no" | "false" | "0" | "maybe"`
: Assigns the function to one of three categories regarding the determinism of functions (relevant to optimization). The value no means the function is deterministic; the value yes means it is proactive; and the value maybe means it is elidable. Requires Saxon-PE or Saxon-EE.

`cache?`
: _boolean_
: Indicates whether the function is to cache its results. Requires Saxon-PE or Saxon-EE.

`saxon:as?`
: _sequence-type_
: Allows additional type information to be supplied using Saxon extension syntax.

`saxon:memo-function?`
: _boolean_
: Specifying yes indicates that Saxon should remember the results of calling the function in a cache, and if the function is called again with the same arguments, the result is retrieved from the cache rather than being recalculated. Requires Saxon-PE or Saxon-EE.

## Notes on the Saxon implementation

Saxon defines an extra attribute on `xsl:function`, namely `saxon:memo-function`. The attribute `saxon:memo-function="yes"` indicates that Saxon should remember the results of calling the function in a cache, and if the function is called again with the same arguments, the result is retrieved from the cache rather than being recalculated.

The extension attribute `saxon:explain` can also be used on an `xsl:function` element. If the attribute has value `yes`, then at compile time Saxon outputs (to the standard error output) a representation of the optimized expression tree for that function.

The attributes `cache` and `new-each-time` are interpreted in Saxon 9.7 (PE or higher) as follows: if the value of `cache` is `yes`, or the value of `new-each-time` is `no`, then the function is implemented as a memo function, in the same way as when the extension attribute `saxon:memo-function` is set. Note that the cache used for a memo function in Saxon 9.7 is always a full cache, that is, it retains the results of all previous function calls within the scope of a query or transformation. In Saxon-HE, these attributes have no effect.

The `visibility` attribute is implemented since Saxon 9.6 as part of the implementation of XSLT 3.0 packages.

Saxon 9.8 introduces support for streamable stylesheet functions, based on the new XSLT 3.0 attribute `streamability`. Test coverage for this feature is rather slim at the time of release.

## Details

In limited circumstances, stylesheet functions (`xsl:function`) optimise tail-recursion. The circumstances are that the `select` expression of the [`xsl:sequence`](xsl-sequence.md) instruction which constitutes the enclosed sequence constructor must contain a call on the same function as the `then` or `else` part of a conditional expression (which may be nested in further conditional expressions). It may require a little care to write functions to exploit this. See the examples below.

## Examples

### Example 1

The following example is not tail-recursive, because the recursive call is within an arithmetic expression: the multiplication takes place on return from the recursive call.

```xslt
<xsl:function name="my:factorial" as="xs:integer">
    <xsl:param name="number" as="xs:integer"/>
    <xsl:sequence
        select="if ($number=0) then 1 else $number * my:factorial($number-1)"/>
</xsl:function>
```

### Example 2

The previous example can be recast in tail-recursive form by adding an extra parameter (which should be set to 1 on the initial call):

```xslt
<xsl:function name="x:factorial">
	<xsl:param name="acc" as="xs:integer?"/>
	<xsl:param name="n" as="xs:integer"/>
	<xsl:sequence as="xs:integer"
		select="if ($n = 1) then $acc
				else x:factorial($acc*$n, \$n - 1)" />
</xsl:function>
```

The call `x:factorial(1, 5)` returns `120`.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-function)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-function)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/function)
