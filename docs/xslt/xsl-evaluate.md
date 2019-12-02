---
description: Allows dynamic evaluation of XPath expressions constructed as a string
---

# xsl:evaluate

Allows dynamic evaluation of XPath expressions constructed as a string.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions, but restricted use in Saxon-HE. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: instruction
- **Content**: ( [`xsl:with-param`](xsl-with-param.md) | [`xsl:fallback`](xsl-fallback.md) )\*
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`xpath`**
: _expression_
: An XPath expression which is evaluated to return the target expression as a string.

`as?`
: _sequence-type_
: Defines the required type of the result of the XPath expression. Defaults to `item()*`.

`base-uri?`
: _{ uri }_
: The base URI for the target expression. Defaults to the base URI of the stylesheet instruction.

`with-params?`
: _expression_
: A map used to supply values for variables in the target expression, if the names are only known dynamically.

`context-item?`
: _expression_
: An XPath expression which is evaluated to determine the context item, position, and size, for evaluation of the target expression.

`namespace-context?`
: _expression_
: An expression returning a node; the in-scope namespaces of this node define the namespace context for the XPath expression. Defaults to the namespace context of the `xsl:evaluate` instruction in the stylesheet.

`schema-aware?`
: _{ boolean }_
: If yes, the XPath expression has access to the schema components imported into the stylesheet.

`saxon:options?`
: _expression_
: May be used to set options specific to the Saxon implementation. The value of the attribute is an expression that evaluates to a map. For details see `saxon:options`.

## Notes on the Saxon implementation

The instruction has been implemented since Saxon 9.3, originally with the restriction that functions available only in XSLT, such as `key()`, could not be used in the target XPath expression. The instruction has been fully implemented since Saxon 9.6. The switch to disable the feature (required by the W3C specification) became available in Saxon 9.8. The `saxon:options` attribute became available in Saxon 9.9.

The instruction is recognized in Saxon-HE, but the feature is "statically disabled", which means that an error occurs if the instruction is actually executed.

If you are concerned about security implications of this feature, you can disable it either statically or dynamically, by setting the configuration property `Feature.DISABLE_XSL_EVALUATE`.

## Details

The `xsl:evaluate` instruction allows dynamic evaluation of XPath expressions in the same way as the `saxon:evaluate()` extension function that has been available in Saxon for many years.

The functionality is available as an XSLT instruction, rather than a function, to allow more flexibility in the syntax, in particular the ability to define parameters using [`xsl:with-param`](xsl-with-param.md) child elements.

The instruction may take an [`xsl:fallback`](xsl-fallback.md) to define fallback behaviour when using an XSLT 2.0 (or 1.0) processor.

_Before using `xsl:evaluate`, consider whether higher-order functions (also new in XSLT 3.0) would provide a better solution to the problem. Also think carefully about the possibility of injection attacks if the expression to be evaluated is formed by string concatenation._

## Examples

Sorting product elements according to a sort key supplied (in the form of an XPath expression) as a parameter to the stylesheet:

```xslt
<xsl:apply-templates select="product">
    <xsl:sort>
        <xsl:evaluate xpath="$product-sort-key"/>
    </xsl:sort>
</xsl:apply-templates>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-evaluate)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/evaluate)

## See also

- [`saxon:evaluate()`](http://saxonica.com/documentation/index.html#!functions/saxon/evaluate)
