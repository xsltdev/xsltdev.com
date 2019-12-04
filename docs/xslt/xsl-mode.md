---
description: Allows properties of a mode to be defined
---

# xsl:mode

Allows properties of a mode to be defined.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

`name?`
: _eqname_
: Identifies the name of this mode; if omitted, the element describes the properties of the unnamed mode.

`streamable?`
: _boolean_
: The value yes indicates that template rules using this mode must be capable of being evaluated in a streaming manner. This imposes restrictions on the content of the template rules. Requires Saxon-EE.

`use-accumulators?`
: _tokens_
: Relevant only when this mode is the initial mode of the transformation. Defines the set of accumulators that are applicable to documents containing nodes in the initial match selection. Available since Saxon 9.7.0.10.

`on-no-match?`
: `"deep-copy" | "shallow-copy" | "deep-skip" | "shallow-skip" | "text-only-copy" | "fail"`
: Indicates what action is taken when a node being processed by [`xsl:apply-templates`](xsl-apply-templates.md) in this mode matches no template rule. The default value is `text-only-copy`. The permitted values are:
: - `text-only-copy`: the XSLT 2.0 behaviour (for elements: apply-templates to the children; for text nodes: copy the text node to the output)
: - `shallow-copy`: invoke the "identity template", which copies an element node and does apply-templates to its attributes and children
: - `deep-copy`: invoke [`xsl:copy-of`](xsl-copy-of.md)
: - `shallow-skip`: ignores this node, does apply-templates to its attributes and children
: - `deep-skip`: ignores this node and all its descendants
: - `fail`: reports a dynamic error

`on-multiple-match?`
: `"use-last" | "fail"`
: Indicates what action is taken when a node being processed by `xsl:apply-templates` in this mode matches more than one template rule (with the same precedence and priority). The values are `fail` indicating that a dynamic error is reported, or `use-last` (the default) indicating that the template rule appearing last in document order is chosen.

`warning-on-no-match?`
: _boolean_
: The value yes causes a run-time warning when a node is matched by no template rules. The default for Saxon is `no`.

`warning-on-multiple-match?`
: _boolean_
: The value yes causes a run-time warning when a node is matched by multiple template rules. The default for Saxon is `yes`.

`typed?`
: _boolean_ | `"strict" | "lax" | "unspecified"`
: Informs the processor whether the nodes to be processed by template rules in this mode are to be typed or untyped. The default is `unspecified`, which places no constraints on the nodes.

`visibility?`
: `"public" | "private" | "final"`
: Determines the potential visibility of the component corresponding to this mode; the default is `private`.

`saxon:trace?`
: _boolean_
: Causes tracing of all template rules executed in the mode, showing the nodes selected by `xsl:apply-templates` and the rules used to process them.

## Details

The `xsl:mode` declaration is new in XSLT 3.0. Previously, modes were declared implicitly by referring to them in the mode attribute of [`xsl:template`](xsl-template.md) or [`xsl:apply-templates`](xsl-apply-templates.md).

The element always appears as a child of [`xsl:stylesheet`](xsl-stylesheet.md) (or [`xsl:transform`](xsl-transform.md)), and it is empty (has no children).

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-mode)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/mode)

## See also

- [`xsl:template`](xsl-template.md)
- [`xsl:apply-templates`](xsl-apply-templates.md)
