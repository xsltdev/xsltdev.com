---
description: Used to define a formal parameter to a template, the stylesheet, a function, or an iteration
---

# xsl:param

Used to define a formal parameter to a template, the stylesheet, a function, or an iteration.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: sequence-constructor
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md); [`xsl:override`](xsl-override.md); [`xsl:function`](xsl-function.md); [`xsl:template`](xsl-template.md); [`xsl:iterate`](xsl-iterate.md)

## Attributes

**`name`**
: _eqname_
: The name of the parameter.

`select?`
: _expression_
: The default value of the parameter may be defined either by a select attribute, or by the contents of the [`xsl:param`](xsl-param.md) element, in the same way as for [`xsl:variable`](xsl-variable.md). The default value is ignored if an actual parameter is supplied with the same name.

`as?`
: _sequence-type_
: Defines the required type of the parameter. The supplied value of the parameter will be converted to this type if required. If the parameter is omitted, the default value must conform to the type. Note that if no default is specified, the default is a zero-length string, which may conflict with the required type.

`required?`
: _boolean_
: Not allowed for function parameters, which are always required. If the parameter is required, no default value may be specified. Failure to supply a value for a required parameter gives a run-time error (the specification says that in the case of [`xsl:call-template`](xsl-call-template.md), it should be a static error).

`tunnel?`
: _boolean_
: The value yes may be specified only for template parameters, and indicates that the parameter is a tunnel parameter. Tunnel parameters are automatically passed on by the called template to any further templates that it calls, and so on recursively. The default is `no`.

`static?`
: _boolean_
: The value yes may be specified only for stylesheet parameters, and indicates that the parameter is a static parameter (that is, its value is known during static analysis of the stylesheet). The default is `no`.

`saxon:as?`
: _sequence-type_
: Allows additional type information to be supplied using Saxon extension syntax.

`saxon:assignable?`
: _boolean_
: May be set on global variables. Setting the value to yes ensures that the variable is actually evaluated, which is useful if the select expression calls extension functions with side-effects; without this, a variable that is never referenced may never be evaluated.

## Notes on the Saxon implementation

It is strongly recommended to use the as attribute to declare the expected type of a parameter. Not only does this help debugging (by catching errors closer to the point where they occur), it also helps the Saxon optimizer generate more efficient code.

_One caveat, however: for a large sequence, map, or array, declaring a precise required type can in some cases trigger expensive run-time type checking. Saxon will try to avoid this but it is not always possible._

XSLT 3.0 introduces static parameters (global parameters declared with `static="yes"`). These are implemented since Saxon 9.5. The value of a static parameter must be known at stylesheet compile time. Static parameters can be referenced in `[xsl:]use-when` attributes, and also in the initializers of other static parameters and variables. The scope rules are a little different from other global variables and parameters - forwards references are not allowed. The values of static parameters may be supplied from the command line in the same way as dynamic parameters; they may also be supplied via a new method call on the s9api `XsltCompiler` object.

In standard XSLT, the value of a global variable cannot be updated once it has been declared using `xsl:param`. Saxon however provides a `saxon:assign` extension element to circumvent this restriction. The extension attribute `saxon:assignable` must be set to yes on the relevant `xsl:param` in order to use this feature.

The `type-information` attribute was removed at Saxon 7.5.

## Details

As a template parameter, xsl:param must be used as an immediate child of the [`xsl:template`](xsl-template.md) element. As a stylesheet parameter, it must be used as an immediate child of the [`xsl:stylesheet`](xsl-stylesheet.md) element.

In XSLT 2.0, `xsl:param` can appear as a child of [`xsl:function`](xsl-function.md), as a function parameter.

In XSLT 3.0, `xsl:param` can also appear as a child of [`xsl:iterate`](xsl-iterate.md), as an iteration parameter.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-param)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-param)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/param.html)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:call-template`](xsl-call-template.md)
- [`xsl:iterate`](xsl-iterate.md)
- [`xsl:variable`](xsl-variable.md)
- [`xsl:with-param`](xsl-with-param.md)
