# Templates (blade, smarty, twig…)

Please refer to [Laravel “Blade Templates” article](http://laravel.com/docs/5.1/blade)
for style–guides about Blade templates.


## Addendum

### Control Structures

Control structures and common code **MUST** be indented with four spaces to avoid indentation weirdness.

**Invalid**

```blade
@if (something)
    @if (somethingElse)
    <div>
        …
    </div>
    @endif

<div>
    …
</div>
@endif
```

**Valid**


```blade
@if (something)
    @if (somethingElse)
        <div>
            …
        </div>
    @endif

    <div>
        …
    </div>
@endif
```


### PHP in templates

#### Echoing values

If having the logic outside the template makes code way more complicated, then:
- ​**either**​ there is a problem in the PHP file (controller, composer…) and we can refactor the code,
- ​**or**​ put the logic in the template, ​**and**​ leave a comment about what prevents the logic to be outside of the template.

#### Writing control structures

Use [alternative syntax for control structures](http://php.net/manual/en/control-structures.alternative-syntax.php):

- Knowing what structure is closed is easier.
- PHP and markup are better kept separated.

Examples:

* NOT OK:

    ```php
    <?php if (…) { ?>
    <!-- some markup… -->

        <?php foreach (…) { ?>
        <!-- some markup… -->
        <?php } ?>

    <!-- some markup… -->
    <?php } ?>
    ```

    ```php
    <?php if (…) {
        echo '<!-- some markup… -->';

        foreach (…) {
            echo '<!-- some markup… -->';
        }

        echo '<!-- some markup… -->';
    } ?>
    ```

* OK:

    ```php
    <?php if (…) : ?>
    <!-- some markup… -->

        <?php foreach (…) : ?>
        <!-- some markup… -->
        <?php endforeach; ?>

    <!-- some markup… -->
    <?php endif; ?>
    ```
