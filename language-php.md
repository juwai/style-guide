# PHP Style Guidelines

We should follow best practices accepted by the community.
As mentioned in _[php the right way][1]_, PHP-FIG, the PHP Framework Interop Group, announced PSR.
Some of the style guides are inspired by [CodeIgniter Framework](https://www.codeigniter.com/user_guide/general/styleguide.html)

We decided to follow [PSR-2].

[1]: http://www.phptherightway.com/
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

---

Quick Links: [SQL Queries](#sql-queries) | [Localized Texts](#localized-texts) | [Debug Codes](#debug-codes) | [Code Sizes](#code-sizes) | [Operators](#operators)

---

## SQL Queries

Although we’re using an ORM, there are cases where complex SQL statements need raw MySQL queries.

When doing raw MySQL query on PHP, all statements MUST follow our current [mysql style guidelines](https://github.com/juwai/style-guide/blob/master/language-sql.md).

```
$query = $this->db->query('
    SELECT
        `foo`,
        `bar`,
        `baz`,
        `foofoo`,
        `foobar` AS `raboof`,
        `foobaz`
    FROM
        `exp_pre_email_addresses`
    WHERE
        `foo` != 'oof'
        AND baz != 'zab'
    ORDER BY `foobaz`
    LIMIT 5 , 100
');
```

## Localized Texts

Any text that is output in the user interface should use language variables in your lang file to allow localization. 

**Valid:**
```
return 'Invalid Selection';
```

**Invalid:**
```
return $this->lang->line('invalid_selection');
```

## Debug Codes

No debugging code **MUST** be left in place in any php files, i.e. no var_dump(), print_r(), die(), and exit() calls must be removed.

## Code Sizes

**Methods** - Class methods that exceed to 10 lines **MUST** be broken down into units that are testable. Violations of this rule usually indicates that the method is doing too much. Try to reduce the method size by creating helper methods and removing any copy/pasted code.

**Classes** - Long Class files are indications that the class may be trying to do too much. Try to break it down, and reduce the size to something manageable. A class with too many methods is probably a good suspect for refactoring, in order to reduce its complexity and find a way to have more fine grained objects.

**Public Members** - A large number of public methods and attributes declared in a class can indicate the class may need to be broken up as increased effort will be required to thoroughly test it. 

## Operators

Starting from PHP 5.3, you can use `?:` to [simplify ternary operations](https://php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary). The two following statements are the same:

```php
$otherVariable = $variable ?: $someVariable;

$otherVariable = $variable ? $variable : $someVariable;
```
