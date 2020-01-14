---
description: Causes navigation from the current element, usually but not necessarily to process its children
---

# xsl:apply-templates

Causes navigation from the current element, usually but not necessarily to process its children. Each selected node is processed using the best-match [`xsl:template`](xsl-template.md) defined for that node.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: ( [`xsl:sort`](xsl-sort.md) | [`xsl:with-param`](xsl-with-param.md) )\*
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: expression
: Sequence of nodes to be processed. If this attribute is omitted, then all the immediate children of the current node are processed.

`mode?`
: token
: Identifies the processing mode. If this attribute is present, only templates with a matching mode parameter will be considered when searching for the rule to apply to the selected elements.

## Notes on the Saxon implementation

In XSLT 3.0, the `xsl:apply-templates` instruction can select atomic values as well as nodes, and the match pattern syntax of [`xsl:template`](xsl-template.md) is extended to allow atomic values as well as nodes to be matched. See Patterns in XSLT 3.0 for more details. All of the extensions to the syntax of match patterns are implemented since Saxon 9.6.

Earlier drafts of XSLT 3.0 introduced a pattern syntax `~typename`: for example `~xs:integer` would match any integer. With experience this was found not to be very useful, and it has been dropped. Instead a new pattern syntax `.[expression]` was introduced: this matches any item for which the effective boolean value of the expression (evaluated with that item as the context item) is true. For example `.[. gt 0]` will match any item (necessarily a number) that is greater than zero, while `.[nilled()]` matches any element that is nilled (`@xsi:nil='true'`). The `~typename` syntax was supported in Saxon 9.5, but not since Saxon 9.6.

For `xsl:apply-templates` to be streamable, the W3C rules require that the `select` expression must be "striding", which essentially means that it may use the child axis but not the descendant axis (to ensure that selected nodes do not overlap each other). Saxon attempts to be more liberal than this, and allow streaming also when the descendant axis is used (the implementation will buffer output in memory if the selected nodes actually overlap). This extension applies only if Saxon streamability extensions are enabled (on the command line or by configuration properties). The equivalent extension for [`xsl:for-each`](xsl-for-each.md) and [`xsl:iterate`](xsl-iterate.md) has been dropped since Saxon 9.6, because it was found to cause problems when local variables were used.

## Details

If the `select` attribute is _omitted_, apply-templates causes all the immediate children of the current node to be processed: that is, child elements and character content, in the order in which it appears. Character content must be processed by a template whose match pattern will be something like `*/text()`. Child elements similarly are processed using the appropriate template, selected according to the rules given under [`xsl:template`](xsl-template.md).

If the `select` attribute is _included_, the result must be a sequence of nodes. All nodes selected by the expression are processed.

The `xsl:apply-templates` element is usually empty, in which case the selected nodes are processed in the order they are selected (this will usually be document order, but this depends on the `select` expression that is used). However the element may include [`xsl:sort`](xsl-sort.md) and/or [`xsl:param`](xsl-param.md) elements:

- For sorted processing, one or more child `xsl:sort` elements may be included. These define the sort order to be applied to the selection. The sort keys are listed in major-to-minor order.
- To supply parameters to the called template, one or more `xsl:with-param` elements may be included. The values of these parameters are available to the called template. If the `xsl:with-param` element specifies `tunnel="yes"`, then the parameter is passed transparently through to templates called at any depth, but it can only be referenced by an `xsl:param` element that also specifies `tunnel="yes"`. If the default value, `tunnel="no"` is used, then the parameter value is available only in the immediately called template, and only if the `xsl:param` element specifies `tunnel="no"` (explicitly or by defaulting the attribute).

The selected nodes are processed in a particular context. This context includes:

- A current node: the node being processed.
- A current node list: the list of nodes being processed, in the order they are processed (this affects the value of the [`position()`](../xpath/position.md) and [`last()`](last.md) functions).
- A set of variables, which initially is those variables defined as parameters.

The full syntax of select expressions is outlined in [XPath Expression Syntax](http://www.saxonica.com/documentation/index.html#!expressions); some examples of the most useful forms of select expression are given in the example below.

## Examples

Some examples of the most useful forms of select expression:

| Expression                         | Meaning                                                                                |
| ---------------------------------- | -------------------------------------------------------------------------------------- |
| `XXX`                              | Process all immediate child elements with tag `XXX`                                    |
| `*`                                | Process all immediate child elements (but not character data within the element)       |
| `../TITLE`                         | Process the `TITLE` children of the parent element                                     |
| `XXX[@AAA]`                        | Process all `XXX` child elements having an attribute named `AAA`                       |
| `@*`                               | Process all attributes of the current element                                          |
| `*/ZZZ`                            | Process all grandchild `ZZZ` elements                                                  |
| `XXX[ZZZ]`                         | Process all child `XXX` elements that have a child `ZZZ`                               |
| `XXX[@WIDTH and not(@width="20")]` | Process all child `XXX` elements that have a `WIDTH` attribute whose value is not `20` |
| `AUTHOR[1]`                        | Process the first child `AUTHOR` element                                               |
| `APPENDIX[@NUMBER][last()]`        | Process the last child `APPENDIX` element having a `NUMBER` attribute                  |
| `APPENDIX[last()][@number]`        | Process the last child `APPENDIX` element provided it has a `NUMBER` attribute         |

## Links to W3C specifications

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-apply-templates)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-apply-templates)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/apply-templates.html)

## See also

- [`xsl:call-template`](xsl-call-template.md)
- [`xsl:sort`](xsl-sort.md)
- [`xsl:template`](xsl-template.md)
- [`xsl:with-param`](xsl-with-param.md)
