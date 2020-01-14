---
description: Used to make assertions in the form of XPath expressions, causing a dynamic error if the assertion turns out to be false
---

# xsl:assert

Used to make assertions in the form of XPath expressions, causing a dynamic error if the assertion turns out to be false.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.5._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

**`test`**
: _expression_
: XPath expression to be asserted.

`select?`
: _expression_
: Can be used to specify (part of) the content of the error message produced when the assertion is false.

`error-code?`
: _{ eqname }_
: Specifies the error code associated with the error message produced when the assertion is false.

## Notes on the Saxon implementation

Following a change in the W3C specification, from Saxon 9.7 assertions are now disabled by default. To enable assertions, use the -ea command line option, or the `Feature.XSLT_ENABLE_ASSERTIONS` configuration property, or call `XsltCompiler.enableAssertions(true)` in the s9api interface.

## Details

It may be useful to add an attribute such as `use-when="$DEBUG"` to `xsl:assert` instructions; the global static variable `DEBUG` can then be used to switch assertion processing on and off. The variable might be declared as `<xsl:variable name="DEBUG" as="xs:boolean" select="true()"/>`.

## Examples

The following code tests whether the value of \$x is non-negative, and if not, fails with an error message:

```xslt
<xsl:assert test="$x &gt; 0">Argument $x must be greater than zero</xsl:assert>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-assert)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/assert.html)
