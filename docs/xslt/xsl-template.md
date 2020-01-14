---
description: Defines a processing rule for source elements or other nodes of a particular type
---

# xsl:template

Defines a processing rule for source elements or other nodes of a particular type.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: ( [`xsl:context-item`](xsl-context-item.md)?, [`xsl:param`](xsl-param.md)*, *sequence-constructor\* )
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl:stylesheet); [`xsl:transform`](xsl-transform.md); [`xsl:override`](xsl-override.md)

## Attributes

`match?`
: _pattern_
: Pattern to identify the type of node to be processed. The most common form of pattern is simply an element name. However, more complex patterns may also be used: the syntax of patterns is given in more detail in XSLT Pattern Syntax. The following examples show some of the possibilities:

| Pattern                       | Meaning                                                                                                                                                                                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `XXX`                         | Matches any element whose name (tag) is `XXX`                                                                                                                                                                                                                    |
| `*`                           | Matches any element                                                                                                                                                                                                                                              |
| `XXX/YYY`                     | Matches any `YYY` element whose parent is an `XXX`                                                                                                                                                                                                               |
| `XXX//YYY`                    | Matches any `YYY` element that has an ancestor named `XXX`                                                                                                                                                                                                       |
| `/*/XXX`                      | Matches any `XXX` element that is immediately below the root (document) element                                                                                                                                                                                  |
| `*[@ID]`                      | Matches any element with an `ID` attribute                                                                                                                                                                                                                       |
| `XXX[1]`                      | Matches any `XXX` element that is the first `XXX` child of its parent element. (Note that this kind of pattern can be very inefficient: it is better to match all `XXX` elements with a single template, and then use [`xsl:if`](xsl-if.md) to distinguish them) |
| `SECTION[TITLE="Contents"]`   | Matches any `SECTION` element whose first `TITLE` child element has the value `Contents`                                                                                                                                                                         |
| `A/TITLE | B/TITLE | C/TITLE` | Matches any `TITLE` element whose parent is of type `A` or `B` or `C`                                                                                                                                                                                            |
| `text()`                      | Matches any character data node                                                                                                                                                                                                                                  |
| `@*`                          | Matches any attribute                                                                                                                                                                                                                                            |
| `/`                           | Matches the document node                                                                                                                                                                                                                                        |

`name?`
: _eqname_
: If this is present, the template may be invoked directly using [`xsl:call-template`](xsl-call-template.md). The `match` attribute then becomes optional.

`priority?`
: _decimal_
: If there are several `xsl:template` elements that all match the same node, the one that is chosen is determined by the optional `priority` attribute: the template with highest priority wins. The priority is written as a floating-point number; the default priority is `1`. If two matching templates have the same priority, the one that appears last in the stylesheet is used.

`mode?`
: _tokens_
: If this is present, the template will only be matched when the same mode is used in the invoking [`xsl:apply-templates`](xsl-apply-templates.md) element. The value can be a list of mode names, indicating that the template matches more than one mode; this list can include the token `#default` to indicate that the template matches the default (unnamed) mode. Alternatively the `mode` attribute can be set to `#all`, to indicate that the template matches all modes. (This can be useful in conjunction with [`xsl:next-match`](xsl-next-match.md); one can write a template rule that matches in all modes, and then call `xsl:next-match` to continue processing in the original mode.)

`as?`
: _sequence-type_
: Defines the required type of the result. The result of evaluating the sequence constructor is converted to this required type using the function conversion rules. The default is `item()*`.

`visibility?`
: `"public" | "private" | "final" | "abstract"`
: New in XSLT 3.0. Determines the potential visibility of the component corresponding to this template; the default is `private`.

`saxon:as?`
: _sequence-type_
: Allows additional type information to be supplied using Saxon extension syntax.

## Notes on the Saxon implementation

The extension attribute `saxon:explain` can be used on an `xsl:template` element. If the attribute has value `yes`, then at compile time Saxon outputs (to the standard error output) a representation of the optimized expression tree for that template.

Saxon-EE 9.8 introduces just-in-time compilation of template rules. With this enabled, the static analysis of a template rule happens only the first time that the rule fires. This dramatically reduces compilation costs for large stylesheets that define many rules for rarely-used elements (the DITA and DocBook stylesheets are typical examples). This has the consequence that static errors in unused rules may go unreported. The feature can therefore be disabled, for example by using `-opt:-j` on the command line.

## Examples

A simple XSLT template for a particular element. This example causes all `<ptitle>` elements in the source document to be output as HTML `<h2>` elements.

```xslt
<xsl:template match="ptitle">
    <h2>
        <xsl:apply-templates/>
    </h2>
</xsl:template>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-template)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-template)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/template)

## See also

- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:apply-imports`](xsl-apply-imports.md)
- [`xsl:call-template`](xsl-call-template.md)
