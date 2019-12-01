# XSLT Elements

XSLT 3.0 Elements reference.

## A

**[`xsl:accept`](xsl-accept.md)**<br />
<small>Allows a package to restrict the visibility of components exposed by a package that it uses.</small>

**[`xsl:accumulator`](xsl-accumulator.md)**<br />
<small>An accumulator defines some processing that is to take place while a document is being sequentially processed: for example, a total that is to be accumulated.</small>

**[`xsl:accumulator-rule`](xsl-accumulator-rule.md)**<br />
<small>Defines a rule for an `xsl:accumulator`</small>

**[`xsl:analyze-string`](xsl-analyze-string.md)**<br />
<small>Applies a regular expression to a supplied string value.</small>

**[`xsl:apply-imports`](xsl-apply-imports.md)**<br />
<small>Searches for a template that matches the current node and that is defined in a stylesheet that was imported (directly or indirectly) from the stylesheet containing the current template, and whose mode matches the current mode.</small>

**[`xsl:analyze-string`](xsl-analyze-string.md)**<br />
<small>Applies a regular expression to a supplied string value.</small>

**[`xsl:apply-imports`](xsl-apply-imports.md)**<br />
<small>Searches for a template that matches the current node and that is defined in a stylesheet that was imported (directly or indirectly) from the stylesheet containing the current template, and whose mode matches the current mode.</small>

**[`xsl:apply-templates`](xsl-apply-templates.md)**<br />
<small>Causes navigation from the current element, usually but not necessarily to process its children. Each selected node is processed using the best-match `xsl:template` defined for that node.</small>

**[`xsl:assert`](xsl-assert.md)**<br />
<small>Used to make assertions in the form of XPath expressions, causing a dynamic error if the assertion turns out to be false.</small>

**[`xsl:attribute`](xsl-attribute.md)**<br />
<small>The `xsl:attribute` element is used to add an attribute value to an `xsl:element` element or literal result element, or to an element created using `xsl:copy`.</small>

**[`xsl:attribute-set`](xsl-attribute-set.md)**<br />
<small>Used to declare a named collection of attributes, which will often be used together to define an output style.</small>

## B

**[`xsl:break`](xsl-break.md)**<br />
<small>The `xsl:break` instruction is used within `xsl:iterate`, and causes premature completion before the entire input sequence has been processed.</small>

## C

**[`xsl:call-template`](xsl-call-template.md)**<br />
<small>Invokes a named template.</small>

**[`xsl:catch`](xsl-catch.md)**<br />
<small>In conjunction with `xsl:try`, the `xsl:catch` instruction allows recovery from dynamic errors.</small>

**[`xsl:character-map`](xsl-character-map.md)**<br />
<small>Defines a named character map for use during serialization.</small>

**[`xsl:choose`](xsl-choose.md)**<br />
<small>Used to choose one of a number of alternative outputs.</small>

**[`xsl:comment`](xsl-comment.md)**<br />
<small>Indicates text that is to be output to the current output stream in the form of an XML or HTML comment.</small>

**[`xsl:context-item`](xsl-context-item.md)**<br />
<small>Used to declare the initial context item for a template: whether the template requires a context item, and if so, what its expected type is.</small>

**[`xsl:copy`](xsl-copy.md)**<br />
<small>Causes the current XML node in the source document to be copied to the output.</small>

**[`xsl:copy-of`](xsl-copy-of.md)**<br />
<small>Copies the value obtained by evaluating the mandatory select attribute. It makes an exact copy.</small>

## D

**[`xsl:decimal-format`](xsl-decimal-format.md)**<br />
<small>Indicates a set of localisation parameters. If the `xsl:decimal-format` element has a name attribute, it identifies a named format; if not, it identifies the default format.</small>

**[`xsl:document`](xsl-document.md)**<br />
<small>Creates a new document node.</small>

## E

**[`xsl:element`](xsl-element.md)**<br />
<small>Used to create an output element whose name might be calculated at run-time.</small>

**[`xsl:evaluate`](xsl-evaluate.md)**<br />
<small>Allows dynamic evaluation of XPath expressions constructed as a string.</small>

**[`xsl:expose`](xsl-expose.md)**<br />
<small>Used to modify the visibility of selected components within a package.</small>

## F

**[`xsl:fallback`](xsl-fallback.md)**<br />
<small>Used to define recovery action to be taken when an instruction element is used in the stylesheet and no implementation of that element is available.</small>

**[`xsl:for-each`](xsl-for-each.md)**<br />
<small>Causes iteration over the nodes selected by a node-set expression.</small>

**[`xsl:for-each-group`](xsl-for-each-group.md)**<br />
<small>Selects a sequence of nodes and/or atomic values and organizes them into subsets called groups.</small>

**[`xsl:fork`](xsl-fork.md)**<br />
<small>The result of the `xsl:fork` instruction is the sequence formed by concatenating the results of evaluating each of its contained instructions, in order.</small>

**[`xsl:function`](xsl-function.md)**<br />
<small>Defines a function within a stylesheet. The function is written in XSLT but it may be called from any XPath expression in the stylesheet. It must have a non-default namespace prefix.</small>

## G

**[`xsl:global-context-item`](xsl-global-context-item.md)**<br />
<small>Used to declare whether a global context item is required, and if so, to declare its required type.</small>

## I

**[`xsl:if`](xsl-if.md)**<br />
<small>Used for conditional processing. It takes a mandatory test attribute, whose value is a boolean expression. The contents of the `xsl:if` element are expanded only of the expression is true.</small>

**[`xsl:import`](xsl-import.md)**<br />
<small>Used to import the contents of one stylesheet module into another.</small>

**[`xsl:import-schema`](xsl-import-schema.md)**<br />
<small>Used to identify a schema containing definitions of types that are referred to in the stylesheet.</small>

**[`xsl:include`](xsl-include.md)**<br />
<small>Used to include the contents of one stylesheet within another.</small>

**[`xsl:iterate`](xsl-iterate.md)**<br />
<small>Used to iterate over a sequence, with the option to set parameters for use in the next iteration.</small>

## K

**[`xsl:key`](xsl-key.md)**<br />
<small>Used at the top level of the stylesheet to declare an attribute, or other value, that may be used as a key to identify nodes using the `key()` function within an expression.</small>

## M

**[`xsl:map`](xsl-map.md)**<br />
<small>Used to construct a new map.</small>

**[`xsl:map-entry`](xsl-map-entry.md)**<br />
<small>Used to construct a singleton map (one key and one value).</small>

**[`xsl:matching-substring`](xsl-matching-substring.md)**<br />
<small>Used within an `xsl:analyze-string` element to indicate the default action to be taken with substrings that match a regular expression.</small>

**[`xsl:merge`](xsl-merge.md)**<br />
<small>The purpose of the instruction is to allow merging of two or more pre-sorted input files, optionally using streamed processing of any or all of the inputs.</small>

**[`xsl:merge-action`](xsl-merge-action.md)**<br />
<small>Used within an `xsl:merge` instruction to define the processing to be carried out on each group of input items sharing a value for the merge key.</small>

**[`xsl:merge-key`](xsl-merge-key.md)**<br />
<small>Used to define the merge keys on which the input sequences of a merging operation are sorted.</small>

**[`xsl:merge-source`](xsl-merge-source.md)**<br />
<small>Describes the input source for an `xsl:merge` instruction.</small>

**[`xsl:message`](xsl-message.md)**<br />
<small>Causes a message to be displayed.</small>

**[`xsl:mode`](xsl-mode.md)**<br />
<small>Allows properties of a mode to be defined.</small>

## N

**[`xsl:namespace`](xsl:namespace)**<br />
<small>Creates a namespace node.</small>

**[`xsl:namespace-alias`](xsl-namespace-alias.md)**<br />
<small>A top-level element used to control the mapping between a namespace URI used in the stylesheet and the corresponding namespace URI used in the result document.</small>

**[`xsl:next-iteration`](xsl-next-iteration.md)**<br />
<small>The `xsl:next-iteration` instruction occurs within `xsl:iterate`. The contents are a set of `xsl:with-param` elements defining the values of the iteration parameters to be used on the next iteration.</small>

**[`xsl:next-match`](xsl-next-match.md)**<br />
<small>Chooses the next template to execute.</small>

**[`xsl:non-matching-substring`](xsl-non-matching-substring.md)**<br />
<small>Used within an `xsl:analyze-string` element to indicate the default action to be taken with substrings that do not match a regular expression.</small>

**[`xsl:number`](xsl-number.md)**<br />
<small>Outputs the sequential number of a node in the source document.</small>

## O

**[`xsl:on-completion`](xsl-on-completion.md)**<br />
<small>Occurs within `xsl:iterate` to define processing to be carried out when the input sequence is exhausted.</small>

**[`xsl:on-empty`](xsl-on-empty.md)**<br />
<small>Used to allow conditional content construction to be made streamable. Outputs the enclosed content only if the containing sequence generates no "ordinary" content.</small>

**[`xsl:on-non-empty`](xsl-on-non-empty.md)**<br />
<small>Used to allow conditional content construction to be made streamable. Outputs the enclosed content only if the containing sequence also generates "ordinary" content.</small>

**[`xsl:otherwise`](xsl-otherwise.md)**<br />
<small>Used within an `xsl:choose` element to indicate the default action to be taken if none of the other choices matches.</small>

**[`xsl:output`](xsl-output.md)**<br />
<small>Used to control the format of serial output files resulting from the transformation.</small>

**[`xsl:output-character`](xsl-output-character.md)**<br />
<small>Used to define the output representation of a given Unicode character, in an `xsl:character-map`.</small>

**[`xsl:override`](xsl-override.md)**<br />
<small>Allows a using package to override selected components from a used package.</small>

## P

**[`xsl:package`](xsl-package.md)**<br />
<small>Defines a set of stylesheet modules that can be compiled as a unit, independently of other packages.</small>

**[`xsl:param`](xsl-param.md)**<br />
<small>Used to define a formal parameter to a template, the stylesheet, a function, or an iteration.</small>

**[`xsl:perform-sort`](xsl-perform-sort.md)**<br />
<small>Takes a sequence as its input and produces a sorted sequence as its output.</small>

**[`xsl:preserve-space`](xsl-preserve-space.md)**<br />
<small>Used at the top level of the stylesheet to define elements in the source document for which whitespace nodes are significant and should be retained.</small>

**[`xsl:processing-instruction`](xsl-processing-instruction.md)**<br />
<small>Causes an XML processing instruction to be output.</small>

## R

**[`xsl:result-document`](xsl-result-document.md)**<br />
<small>Used to direct output to a secondary output destination.</small>

## S

**[`xsl:sequence`](xsl-sequence.md)**<br />
<small>Used to construct arbitrary sequences. It may select any sequence of nodes and/or atomic values, and essentially adds these to the result sequence.</small>

**[`xsl:sort`](xsl-sort.md)**<br />
<small>Used within an `xsl:for-each`, `xsl:apply-templates`, `xsl:for-each-group`, or `xsl:perform-sort` to indicate the order in which the selected elements are processed.</small>

**[`xsl:source-document`](xsl-source-document.md)**<br />
<small>Used to initiate streamed or unstreamed processing of a source document.</small>

**[`xsl:stream`](xsl-stream.md)**<br />
<small>Used to initiate streamed processing of a source document.</small>

**[`xsl:strip-space`](xsl-strip-space.md)**<br />
<small>Used at the top level of the stylesheet to define elements in the source document for which whitespace nodes are insignificant and should be removed from the tree before processing.</small>

**[`xsl:stylesheet`](xsl-stylesheet.md)**<br />
<small>The `xsl:stylesheet` element is always the top-level element of an XSLT stylesheet. The name `xsl:transform` may be used as a synonym.</small>

## T

**[`xsl:template`](xsl-template.md)**<br />
<small>Defines a processing rule for source elements or other nodes of a particular type.</small>

**[`xsl:text`](xsl-text.md)**<br />
<small>Causes its content to be output.</small>

**[`xsl:transform`](xsl-transform.md)**<br />
<small>The name `xsl:transform` is a synonym for `xsl:stylesheet`.</small>

**[`xsl:try`](xsl-try.md)**<br />
<small>In conjunction with `xsl:catch`, the `xsl:try` instruction allows recovery from dynamic errors occurring within the expression it wraps.</small>

## U

**[`xsl:use-package`](xsl-use-package.md)**<br />
<small>Used to allow components of one package to be referenced within another.</small>

## V

**[`xsl:value-of`](xsl-value-of.md)**<br />
<small>Evaluates an expression as a string, and outputs its value to the current result tree.</small>

**[`xsl:variable`](xsl-variable.md)**<br />
<small>Used to declare a variable and give it a value.</small>

## W

**[`xsl:when`](xsl-when.md)**<br />
<small>Used within an `xsl:choose` element to indicate one of a number of choices.</small>

**[`xsl:where-populated`](xsl-where-populated.md)**<br />
<small>Used to allow conditional content construction to be made streamable. Used to avoid outputting a wrapper element if it would have no children.</small>

**[`xsl:with-param`](xsl-with-param.md)**<br />
<small>Used to define an actual parameter to a template: within an `xsl:call-template`, `xsl:apply-templates`, `xsl:apply-imports`, or `xsl:next-match` element.</small>
