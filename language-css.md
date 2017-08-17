## Cascading Style Sheets

### Coding conventions

Please refer to [stylelint-config-juwai](https://github.com/juwai/stylelint-config-juwai/blob/master/index.js) for style–guides about CSS.

### Avoid selector name concatenation in SCSS/LESS

Name concatenation decreases code readability and makes codebase hard to search.

**Bad:**

```css
.c-figures {
    &__title {
        text-align: right;
        width: 120px;
    }
}
```

**Good:**

```css
.c-figures {
    .c-figures__title {
        text-align: right;
        width: 120px;

        &:hover {
            color: red;
        }
    }
}
```

### Flexbox

Encourage to use flexbox as long as layout and functionality consistent with other modern browsers.
