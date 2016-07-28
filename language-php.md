# PHP Style Guidelines

We should follow best practices accepted by the community.
As mentioned in _[php the right way][1]_, PHP-FIG, the PHP Framework Interop Group, announced PSR.

We decided to follow [PSR-2].

[1]: http://www.phptherightway.com/
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

## SQL Queries
MySQL keywords are always capitalized: SELECT, INSERT, UPDATE, WHERE, AS, JOIN, ON, IN, etc. Break up long queries into multiple lines for legibility, preferably breaking for each clause.

```
INCORRECT:
// keywords are lowercase and query is too long for
// a single line (... indicates continuation of line)
$query = $this->db->query("select foo, bar, baz, foofoo, foobar as raboof, foobaz from exp_pre_email_addresses
...where foo != 'oof' and baz != 'zab' order by foobaz limit 5, 100");

CORRECT:
$query = $this->db->query("SELECT foo, bar, baz, foofoo, foobar AS raboof, foobaz
				FROM exp_pre_email_addresses
				WHERE foo != 'oof'
				AND baz != 'zab'
				ORDER BY foobaz
				LIMIT 5, 100");
```

## Localized Text

Any text that is output in the control panel should use language variables in your lang file to allow localization.

```
INCORRECT:
return "Invalid Selection";

CORRECT:
return $this->lang->line('invalid_selection');
```

## Debugging Code

No debugging code can be left in place for submitted add-ons unless it is commented out, i.e. no var_dump(), print_r(), die(), and exit() calls that were used while creating the add-on, unless they are commented out.

```
// print_r($foo);
```

## TRUE, FALSE, and NULL

TRUE, FALSE, and NULL keywords should always be fully lowercase.

```
CORRECT:
if ($foo == true)
$bar = false;
function foo($bar = null)

INCORRECT:
if ($foo == TRUE)
$bar = FALSE;
function foo($bar = NULL)
```

## Code Size

**Methods** - Class methods that exceeds to 10 lines MUST be broken down into units that are testable. Violations of this rule usually indicate that the method is doing too much. Try to reduce the method size by creating helper methods and removing any copy/pasted code.

**Classes** - Long Class files are indications that the class may be trying to do too much. Try to break it down, and reduce the size to something manageable. A class with too many methods is probably a good suspect for refactoring, in order to reduce its complexity and find a way to have more fine grained objects.

**Public Members** - A large number of public methods and attributes declared in a class can indicate the class may need to be broken up as increased effort will be required to thoroughly test it.

## Operators

Starting from PHP 5.3, you can use `?:` to [simplify ternary operations](https://php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary). The two following statements are the same:

```php
$otherVariable = $variable ?: $someVariable;

$otherVariable = $variable ? $variable : $someVariable;
```
