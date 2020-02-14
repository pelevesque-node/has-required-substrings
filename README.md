[![Build Status](https://travis-ci.org/pelevesque/has-required-substrings.svg?branch=master)](https://travis-ci.org/pelevesque/has-required-substrings)
[![Coverage Status](https://coveralls.io/repos/github/pelevesque/has-required-substrings/badge.svg?branch=master)](https://coveralls.io/github/pelevesque/has-required-substrings?branch=master)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# has-required-substrings

Checks if a string has required substrings.

## Related Packages

https://github.com/pelevesque/has-required-substrings-at-indexes  
https://github.com/pelevesque/has-required-substrings-after-sums      
https://github.com/pelevesque/has-prohibited-substring   
https://github.com/pelevesque/has-prohibited-substring-at-indexes  
https://github.com/pelevesque/has-prohibited-substring-after-sums  

## Node Repository

https://www.npmjs.com/package/@pelevesque/has-required-substrings

## Installation

`npm install @pelevesque/has-required-substrings`

## Tests

Command                      | Description
---------------------------- | ------------
`npm test` or `npm run test` | All Tests Below
`npm run cover`              | Standard Style
`npm run standard`           | Coverage
`npm run unit`               | Unit Tests

## Usage

### Parameters

```js
str                       (required)
requiredSubstrings        (required)
allowLastSubstringToBleed (optional) default = false
```

### Requiring

```js
const hasRequiredSubstrings = require('@pelevesque/has-required-substrings')
```

### Basic Usage

`requiredSubstrings` is an array of substrings. `true` is returned if all
substrings are found.

```js
const str = 'abcde'
const requiredSubstrings = ['f']
const result = hasRequiredSubstrings(str, requiredSubstrings)
// result === false
```

```js
const str = 'abcde'
const requiredSubstrings = ['a']
const result = hasRequiredSubstrings(str, requiredSubstrings)
// result === true
```

```js
const str = 'abcde'
const requiredSubstrings = ['a', 'b', 'f']
const result = hasRequiredSubstrings(str, requiredSubstrings)
// result === false
```

```js
const str = 'abcde'
const requiredSubstrings = ['a', 'b', 'c']
const result = hasRequiredSubstrings(str, requiredSubstrings)
// result === true
```

```js
const str = 'a man a plan a canal'
const requiredSubstrings = ['man', 'plan', 'canal']
const result = hasRequiredSubstrings(str, requiredSubstrings)
// result === true
```

### Options

#### allowLastSubstringToBleed

The `allowLastSubstringToBleed` option is `false` by default. It it used when you want
to allow the last substring to be incomplete if the string is too short.
In the following example, the last substring `canal` starts at the correct index,
but remains incomplete since the string ends. Normally this would return `false`.
With `allowLastSubstringToBleed` set to `true`, it returns `true`.

```js
const str = 'a man a plan a c'
const requiredSubstrings = ['man', 'plan', 'canal']
const allowLastSubstringToBleed = true
const result = hasRequiredSubstrings(str, requiredSubstrings, allowLastSubstringToBleed)
// result === true
```

##### options style

For style compatibility with related packages like `has-required-substrings-after-sums`,
it is possible to set `allowLastSubstringToBleed` using an options style.

```js
const str = 'a man a plan a c'
const requiredSubstrings = ['man', 'plan', 'canal']
const allowLastSubstringToBleed = true
const result = hasRequiredSubstrings(str, requiredSubstrings, {
  allowLastSubstringToBleed: allowLastSubstringToBleed
})
// result === true
```
