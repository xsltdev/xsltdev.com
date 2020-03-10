---
description: Evaluates an expression as a string, and outputs its value to the current result tree
---

# xsl:value-of

Evaluates an expression as a string, and outputs its value to the current result tree.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: _expression_
: Identifes the expression. If this is not specified, the value to be output is obtained by evaluating the sequence constructor contained within the `xsl:value-of` element. The full syntax of expressions is outlined in XPath Expression Syntax. Here are some examples of expressions that can be used in the `select` attribute:

| Expression                | Value                                                                                                                             |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `TITLE`                   | The character content of the first child `TITLE` element if there is one                                                          |
| `@NAME`                   | The value of the `NAME` attribute of the current element if there is one                                                          |
| `.`                       | The expanded character content of the current element                                                                             |
| `../TITLE`                | The expanded character content of the first `TITLE` child of the parent element, if there is one                                  |
| `ancestor::SECTION/TITLE` | The expanded character content of the first `TITLE` child of the enclosing `SECTION` element, if there is one                     |
| `ancestor::*/TITLE`       | The expanded character content of the first `TITLE` child of the nearest enclosing element that has a child element named `TITLE` |
| `PERSON[@ID]`             | The content of the first child `PERSON` element having an `ID` attribute, if there is one                                         |
| `*[last()]/@ID`           | The value of the `ID` attribute of the last child element of any type, if there are any                                           |
| `.//TITLE`                | The content of the first descendant `TITLE` element if there is one                                                               |
| `sum(*/@SALES)`           | The numeric total of the values of the `SALES` attributes of all child elements that have a `SALES` attribute                     |

`separator?`
: _{ string }_
: The separator defaults to a single space if the `select` attribute is used, or to a zero-length string if a sequence constructor is used. The `separator` attribute may be specified as an attribute value template.

`[disable-output-escaping]?`
: _boolean_
: If set to `yes`, special characters such as "`<`" and "`&`" will be output as themselves, not as entities. Be aware that in general this can produce non-well-formed XML, HTML, or JSON. It is useful, however, when generating things such as ASP or JSP pages. The default is `no`.

## Details

If the `select` expression evaluates to a sequence containing more than one item, the result depends on whether a `separator` attribute is present. If the `separator` is absent when running in 1.0 mode, then only the first item is considered. When running in 2.0 mode, all the items are output. The `separator` defaults to a single space if the `select` attribute is used, or to a zero-length string if a sequence constructor is used.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-value-of)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-value-of)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/value-of.html)

## See also

- [`xsl:copy-of`](xsl-copy-of.md)
- [`xsl:text`](xsl-text.md)
