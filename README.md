
# flat-options

[![npm](https://img.shields.io/npm/v/flat-options.svg)](https://www.npmjs.com/package/flat-options)
[![license](https://img.shields.io/npm/l/flat-options.svg)](https://www.npmjs.com/package/flat-options)

> One-level options with default values and validation

Utility function to merge one-level options with default values and perform validation.

## Comparison to `Object.assign`
Unlike `Object.assign` there are some features:

* auto-excluding `undefined` values (useful for conditional options):
  ```js
  const defaults = {foo: 'bar'};
  const options = {foo: undefined};
  Object.assign({}, defaults, options); // -> {foo: undefined}
  // vs
  flatOptions(options, defaults); // -> {foo: 'bar'}
  ```
  
* auto-validation of option keys:
  ```js
  const defaults = {foo: 'bar'};
  const options = {unknown: 'baz'};
  Object.assign({}, defaults, options); // -> {foo: 'bar', unknown: 'baz'}
  // vs
  flatOptions(options, defaults); // -> throws error "Unknown option"!
  ```


## Installation
```bash
npm install --save flat-options
```

## Usage
```js
import flatOptions from 'flat-options';

const defaults = {
  a: 1,
  b: false
};

class Foo {
  constructor(options) {
    this._options = flatOptions(options, defaults);
  }
}

const foo = new Foo({a: 2}); // foo._options will be {a: 2, b: false} 
```

## Related projects
* [defaults](https://www.npmjs.com/package/defaults)
* [lodash.defaults](https://www.npmjs.com/package/lodash.defaults)

## License
MIT @ [Vitaliy Potapov](https://github.com/vitalets)
