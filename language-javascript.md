# JavaScript

Please refer to [airbnb/javascript](https://github.com/airbnb/javascript) and
[eslint-config-juwai](https://github.com/juwai/eslint-config-juwai/blob/master/index.js) for style–guides about JavaScript.

## Addendum

### Whitespace

Use soft tabs (space character) set to 4 spaces.

### Strings

Avoid to have more than 120 characters per line.

### Fix errors early.

We want to **target bugs as soon as possible**. To do so, we should always add
`'use strict';` as the first statement of any function at the root of the
document if you are not using ES6.

### Be more flexible.

In case of a function doing too much but that can‘t be easily refactored, and
if that function has more than two parameters, let’s avoid having the following:
```js
/** Defining this awesome function that does too much.
 *
 * @param {integer} parameter1 - Represent something.
 * @param {integer} parameter2 - Represent something else.
 * @param {boolean} parameter3 - Is this for real?
 * @param {string}  parameter4 - Values for that other stuff.
 */
someFunctionWithAddedParametersOverTime( parameter1, parameter2, parameter3, parameter4 ) {
    // Do something…
    […]
}

// Call the function.
someFunctionWithAddedParametersOverTime(
    undefined,
    undefined,
    false,
    'someValue'
);
```

Use an `options` parameter instead to allow more flexibility:
```js
/** Defining this awesome function that still does too much.
 *
 * @param {object}  options
 * @param {integer} options.parameter1 - Represent something.
 * @param {integer} options.parameter2 - Represent something else.
 * @param {boolean} options.parameter3 - Is this for real?
 * @param {string}  options.parameter4 - Values for that other stuff.
 */
someFunctionWithOptions( options ) {
    // Do something…
    […]
}

// Call the function.
someFunctionWithOptions({
    'parameter4' => 'someValue'
});
```

Ideally: refactor the function into smaller pieces.

## Tools

You can use them in your environment with the relevant tools or plugins:

* ESLint: http://eslint.org/
