---
description: Outputs the sequential number of a node in the source document
---

# xsl:number

Outputs the sequential number of a node in the source document.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- Category: instruction
- Content: none
- Permitted parent elements: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`value?`
: _expression_
: Used to format a number obtained from an expression. If this attribute is present, the `count`, `level`, and `from` attributes are ignored.

`select?`
: _expression_
: If present, this is an expression that selects the node to be numbered. The default is `"."`, the context node.

`level?`
: `"single" | "multiple" | "any"`
: Defines the rules for calculating a number. The default is `single`. For details see the `from` attribute description.

`count?`
: _pattern_
: Pattern indicating which nodes to count; the default is to match all nodes of the same type and name as the current node.

`from?`
: _pattern_
: Pattern whose exact meaning depends on the level. The calculation is as follows:
: `level="single"`<br />If the current node matches the pattern, the counted node is the current node. Otherwise the counted node is the innermost ancestor of the current node that matches the pattern. If no ancestor matches the pattern, the result is zero. If the `from` attribute is present, the counted node must be a descendant of a node that matches the `from` pattern. The result is one plus the number of elder siblings of the counted node that match the `count` pattern.
: `level="any"`<br />The result is the number of nodes in the document that match the `count` pattern, that are at or before the current node in document order, and that follow in document order the most recent node that matches the `from` pattern, if any. Typically this is used to number, say, the diagrams or equations in a document, or in some section or chapter of a document, regardless of where the diagrams or equations appear in the hierarchic structure.
: `level="multiple"`<br />The result of this is not a single number, but a list of numbers. There is one number in the list for each ancestor of the current element that matches the `count` pattern and that is a descendant of the anchor element. Each number is one plus the number of elder siblings of the relevant element that match the `count` pattern. The order of the numbers is "outwards-in".

`format?`
: _{ string }_
: Controls the output format. This contains an alternating sequence of format-tokens and punctuation-tokens. A format-token is any sequence of alphanumeric characters, a punctuation-token is any other sequence. The following values (among others) are supported for the format-token:
: - `1`<br />Sequence 1, 2, 3, ... 10, 11, 12, ...
: - `001`<br />Sequence 001, 002, 003, ... 010, 011, 012, ... (any number of leading zeroes)
: - `a`<br />Sequence a, b, c, ... aa, ab, ac, ...
: - `A`<br />Sequence A, B, C, ... AA, AB, AC, ...
: - `i`<br />Sequence i, ii, iii, iv, ... x, xi, xii, ...
: - `I`<br />Sequence I, II, III, IV, ... X, XI, XII, ...
: There is also support for various Japanese sequences (Hiragana, Katakana, and Kanji) using the format tokens `&#x3042`, `&#x30a2`, `&#x3044`, `&#x30a4`, `&#x4e00`, and for Greek and Hebrew sequences.
: The format token "w" gives the sequence "one", "two", "three", ... , while "W" gives the same in upper-case, and "Ww" in title case. The language is determined by the lang attribute, for example `lang="en"` for English (the default).
: The default format is `"1"`.
: A sequence of Unicode digits other than ASCII digits (for exaple, Tibetan digits) can be used, and will result in decimal numbering using those digits.
: Similarly, any other character classified as a letter can be used, and will result in "numbering" using all consecutive Unicode letters following the one provided. For example, specifying "x" will give the sequence x, y, z, xx, xy, xz, yx, yy, yz, etc. Specifying the Greek letter alpha (`&#178;`) will cause "numbering" using the Greek letters up to "Greek letter omega with tonos" (`&#206;`). Only "i" and "I" (for roman numbering), and the Japanese characters listed above, are exceptions to this rule.
: Successive format-tokens in the format are used to process successive numbers in the list. If there are more format-tokens in the format than numbers in the list, the excess format-tokens and punctuation-tokens are ignored. If there are fewer format-tokens in the format than numbers in the list, the last format-token and the punctuation-token that precedes it are used to format all excess numbers, with the final punctuation-token being used only at the end.
: This character may be preceded or followed by arbitrary punctuation (anything other than these characters or XML special characters such as `"<"`) which is copied to the output verbatim. For example, the value 3 with format `"(a)"` produces output `"(c)"`.

`lang?`
: _{ language }_
: Specifies which language's conventions are used when numbering sequences are language-sensitive (for instance the sequence selected by the tokens "w", "W" and "Ww"), for example `lang="en"` for English (the default). In Saxon-PE and EE, if the ICU localization library JAR file (provided with the distributions) has been loaded, then language support is provided using facilities from ICU - International Components for Unicode as described in Numbers and Dates from ICU. Otherwise, a selection of languages are supported directly, and it is possible to add support for others, using `Numberer` classes as described in Localizing numbers and dates.

`letter-value?`
: _{ "alphabetic" | "traditional" }_
: Disambiguates between numbering sequences that use letters, since in many languages there are two commonly used systems. The value `alphabetic` specifies the alphabetic sequence; the value `traditional` specifies another sequence (for example, in English, this corresponds to the roman numbering specified by the token "i").

`ordinal?`
: _{ string }_
: Indicates whether cardinal or ordinal numbers are required.

`start-at?`
: _{ integer }_
: New in XSLT 3.0. Allows numbering to start at a number other than one. Since 9.7, this can be a sequence of integers.

`grouping-separator?`
: _{ char }_
: Specifies the grouping separator (for example, thousands) used in decimal numbering sequences.

`grouping-size?`
: _{ integer }_
: Specifies the size of the grouping used in decimal numbering sequences (for example, the value `"3"` means thousands).

## Notes on the Saxon implementation

The attribute `start-at` is new in XSLT 3.0 and implemented since Saxon 9.5.

Saxon-EE 9.8 contains a new optimization of `<xsl:number level="any">`, based on XSLT 3.0 accumulators. Provided the parameters of the instruction are context-free (and with various other conditions, for example the nodes being numbered must not be attributes or namespaces), Saxon will evaluate the sequence numbers using an accumulator, which means that all the nodes in a document are numbered in a single pass, rather than each execution of `xsl:number` requiring a backwards search through the document.

In XSLT 3.0 some of the capabilities of the `xsl:number` instruction - specifically the formatting capabilities - are more conveniently packaged via the new [`format-integer()`](../xpath/fn-format-integer.md) function, which is also available in XPath and XQuery.

## Details

With large numbers, the digits may be split into groups. For example, specify `grouping-size="3"` and `grouping-separator="/"` to have the number `3000000` displayed as `"3/000/000"`.

Negative numbers are always output in conventional decimal notation, regardless of the format specified.

## Examples

### Example 1

Format examples:

| Number(s) | Format  | Result    |
| --------- | ------- | --------- |
| `3`       | `(1)`   | `(3)`     |
| `12`      | `I`     | `XII`     |
| `2,3`     | `1.1`   | `2.3`     |
| `2,3`     | `1(i)`  | `2(iii)`  |
| `2,3`     | `1.`    | `2.3.`    |
| `2,3`     | `A.1.1` | `B.3.`    |
| `2,3,4,5` | `1.1`   | `2.3.4.5` |

## Example 2

The following outputs the title child of an `<H2>` element preceded by a composite number formed from the sequential number of the containing `<H1>` element and the number of the containing `<H2>` element.

```xslt
<xsl:template match="H2/TITLE">
    <xsl:number count="H1">.<xsl:number count="H2">
    <xsl:text> </xsl:text>
    <xsl:apply-templates/>
</xsl:template>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-number)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-number)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/number.html)

## See also

- [`format-integer()`](../xpath/fn-format-integer.md)
- [`xsl:decimal-format`](xsl-decimal-format.md)
