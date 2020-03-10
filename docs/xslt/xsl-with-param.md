---
description: Used to define an actual parameter to a template
---

# xsl:with-param

Used to define an actual parameter to a template: within an [`xsl:call-template`](xsl-call-template.md), [`xsl:apply-templates`](xsl-apply-templates.md), [`xsl:apply-imports`](xsl-apply-imports.md), or [`xsl:next-match`](xsl-next-match.md) element. Also used to define parameters to an iteration (using [`xsl:next-iteration`](xsl-next-iteration.md)) or to a dynamic invocation of an XPath expression (using [`xsl:evaluate`](xsl-evaluate.md)).

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:apply-templates`](xsl-apply-templates.md) ; [`xsl:apply-imports`](xsl-apply-imports.md) ; [`xsl:call-template`](xsl-call-template.md) ; [`xsl:evaluate`](xsl-evaluate.md) ; [`xsl:next-match`](xsl-next-match.md) ; [`xsl:next-iteration`](xsl-next-iteration.md)

## Attributes

**`name`**
: _eqname_
: The name of the parameter.

`select?`
: expression
: The value of the parameter may be defined either by a select attribute, or by the contents of the [`xsl:param`](xsl-param.md) element, in the same way as for [`xsl:variable`](xsl-variable.md).

`as?`
: _sequence-type_
: Defines the required type of the parameter. The supplied value of the parameter will be converted to this type if required.

`tunnel?`
: _boolean_
: Used only when passing parameters to templates. The attribute `tunnel="yes"` creates a tunnel parameter which is accessible to called templates at any depth, whether or not they are declared in intermediate templates. However, the value is only accessible if `tunnel="yes"` is also specified on the corresponding `xsl:param` element.

`saxon:as?`
: _sequence-type_
: Allows additional type information to be supplied using Saxon extension syntax.

## Details

For an example, see [`xsl:template`](xsl-template.md).

The parameter has no effect unless the called template includes a matching `xsl:param` element. But when using `xsl:call-template`, it is an error to specify a parameter that isn't declared in the target template, or to omit a parameter that's described in the target template with `required="yes"`.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-with-param)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-with-param)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/with-param.html)

## See also

- [`xsl:apply-imports`](xsl-apply-imports.md)
- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:call-template`](xsl-call-template.md)
- [`xsl:param`](xsl-param.md)
