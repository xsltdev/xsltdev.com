# fn:accumulator-after

Returns the post-descent value of the selected accumulator at the context node. See [`xsl:accumulator`](/xslt/xsl-accumulator/) for more on accumulators.

> Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6.

```
accumulator-after($name as xs:string) ➔ item()*
```

## Arguments

**`$name`**
: `xs:string` The name of the accumulator

## Result

`item()*`

## Namespace

`http://www.w3.org/2005/xpath-functions`

## Links to W3C specifications

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#func-accumulator-after)

## See also

- [`fn:accumulator-before()`](fn-accumulator-before.md)
