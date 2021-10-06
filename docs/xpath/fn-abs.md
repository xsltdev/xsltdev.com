# fn:abs

Returns the absolute value of a given number. Returns the same type as the supplied argument.

> Available in XPath 2.0, XSLT 2.0, XQuery 1.0, and later versions. Available in all Saxon editions.

```
abs($arg as xs:numeric?) ➔ xs:numeric?
```

## Arguments

**`$arg`**
: `xs:numeric?` The input value

## Result

`xs:numeric?`

## Namespace

`http://www.w3.org/2005/xpath-functions`

## Links to W3C specifications

- [XPath 2.0 Functions and Operators](https://www.saxonica.com/documentation11/xpath20abs)
- [XPath 3.0 Functions and Operators](http://www.w3.org/TR/xpath-functions-30/#func-abs)
- [XPath 3.1 Functions and Operators](http://www.w3.org/TR/xpath-functions-31/#func-abs)

# Notes on the Saxon implementation

Saxon also (for compatibility) implements the function [`math:abs()`](math-abs.md) in namespace `http://exslt.org/math`.
