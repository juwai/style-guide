# Global styles

These style–guides apply on any language (if relevant to this language).


## Operators

When splitting a statement on multiple lines, put the operator at the start of the line. This improves readability because:

- operators are aligned and easy to find.
- we know what the current operation is and its argument, all in one line.

This is **not OK**:

```php
// Concatenation
$otherVariable = $variable . someFunction( $parameters ) .
$someVariable;

$otherVariable = $variable . someFunction( $parameters ) .
    $someVariable;

$otherVariable = $variable . someFunction( $parameters )
    . $someVariable;

// Ternary operations
$otherVariable = true ?
    someFunction( $parameters ) :
    $someVariable

$otherVariable = true ? someFunction( $parameters )
    : $someVariable
```

This is **OK**:

```php
// Concatenation
$otherVariable = $variable
    . someFunction( $parameters )
    . $someVariable;

$otherVariable = $variable . someFunction( $parameters ) . $someVariable;

// Ternary operations
$otherVariable = true
    ? someFunction( $parameters )
    : $someVariable
```


## Regular expressions

Comment your regular expressions to explain what they do. We’re not bots!
You can link to an article explaining it or explain it yourself.
