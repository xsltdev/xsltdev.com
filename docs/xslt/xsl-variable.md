---
description: Used to declare a variable and give it a value
---

# xsl:variable

Used to declare a variable and give it a value. If it appears at the top level (immediately within [`xsl:stylesheet`](xsl-stylesheet.md)) it declares a global variable, otherwise it declares a local variable that is visible only within the stylesheet element containing the **`xsl:variable`** declaration. The value of a variable can be referenced within an expression using the syntax `$name`.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:package`](xsl-package.md) ; [`xsl:stylesheet`](xsl-stylesheet.md) ; [`xsl:transform`](xsl-transform.md) ; [`xsl:override`](xsl-transform.md) ; [`xsl:function`](xsl-function.md) ; any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`name`**
: _eqname_
: Defines the name of the variable.

`select?`
: _expression_
: The value of the variable may be defined either by an expression within the optional `select` attribute, or by the contents of the `xsl:variable` element. In the latter case the result is a temporary tree. A temporary tree can be used like a source document, for example it can be accessed using path expressions and processed using template rules.

`as?`
: _sequence-type_
: Defines the required type of the variable. The supplied value of the variable will be converted to this type if required.

`static?`
: _boolean_
: The value `yes` may be specified only for global variables (not local variables), and indicates that the variable is a static variable (that is, its value is known during static analysis of the stylesheet). The default is `no`.

`visibility?`
: `"public" | "private" | "final" | "abstract"`
: New in XSLT 3.0. Allowed only for global variables (not local variables). Determines the potential visibility of the component corresponding to this variable; the default is `private`.

`saxon:as?`
: _sequence-type_
: Allows additional type information to be supplied using Saxon extension syntax.

`saxon:assignable?`
: _boolean_
: May be set on global variables. Setting the value to `yes` ensures that the variable is actually evaluated, which is useful if the `select` expression calls extension functions with side-effects; without this, a variable that is never referenced may never be evaluated.

## Notes on the Saxon implementation

In standard XSLT, variables once declared cannot be updated. Saxon however provides a `saxon:assign` extension element to circumvent this restriction. The extension attribute `saxon:assignable` must be set to yes on the `xsl:variable` in order to use this feature.

## Examples

```xslt
<xsl:stylesheet>
<xsl:variable name="title">A really exciting document</xsl:variable>
<xsl:variable name="backcolor" expr="'#FFFFCC'" />
<xsl:template match="/*">
    <HTML><TITLE><xsl:value-of select="$title"/></TITLE>
    <BODY BGCOLOR='{$backcolor}'>
	    <!-- ... -->
    </BODY></HTML>
</xsl:template>
</xsl:stylesheet>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-variable)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-variable)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/variable.html)

## See also

- [`xsl:param`](xsl-param.md)
