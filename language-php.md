# PHP Style Guidelines

We should follow best practices accepted by the community.
As mentioned in _[php the right way][1]_, PHP-FIG, the PHP Framework Interop Group, announced PSR.

We decided to follow [PSR-2].

[1]: http://www.phptherightway.com/
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

## Operators

Starting from PHP 5.3, you can use `?:` to [simplify ternary operations](https://php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary). The two following statements are the same:

```php
$otherVariable = $variable ?: $someVariable;

$otherVariable = $variable ? $variable : $someVariable;
```

Please read [Global Styles](https://github.com/juwai/style-guide/blob/master/language-global.md) for additional guidelines regarding operators

## Naming

### Variables

We use camelCase for variable names. The first letter should be lowercase.

No:

```php
$variable_name
```

No:

```php
$VariableName
```

Yes:

```php
$variableName
```

### Function (Only PHP7)
We declare function parameter type and return type.
```php
function func(string $param):string
{
    return $param;
}
```

## Templates

Please read [Template Guidelines](https://github.com/juwai/style-guide/blob/master/language-template.md)
