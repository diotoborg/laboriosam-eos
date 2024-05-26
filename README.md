# @diotoborg/laboriosam-eos <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2015 spec-compliant `Array.prototype.copyWithin` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.copyWithin` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var copyWithin = require('@diotoborg/laboriosam-eos');
var assert = require('assert');

var arr = [1, 2, 3, 4, 5];
assert.deepEqual(copyWithin(arr, 0, 3), [4, 5, 3, 4, 5]);
assert.deepEqual(arr, [4, 5, 3, 4, 5]);
```

```js
var copyWithin = require('@diotoborg/laboriosam-eos');
var assert = require('assert');
/* when Array#copyWithin is not present */
delete Array.prototype.copyWithin;
var shimmedCopyWithin = copyWithin.shim();
assert.deepStrictEqual(shimmedCopyWithin, copyWithin.getPolyfill());

var arr = [1, 2, 3, 4, 5];
assert.deepEqual(copyWithin(arr, 0, 3), [4, 5, 3, 4, 5]);
assert.deepEqual(arr, [4, 5, 3, 4, 5]);
```

```js
var copyWithin = require('@diotoborg/laboriosam-eos');
var assert = require('assert');
/* when Array#copyWithin is present */
var shimmedCopyWithin = copyWithin.shim();
assert.equal(shimmedCopyWithin, Array.prototype.copyWithin);

var arr = [1, 2, 3, 4, 5];
assert.deepEqual(copyWithin(arr, 0, 3), [4, 5, 3, 4, 5]);
assert.deepEqual(arr, [4, 5, 3, 4, 5]);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/laboriosam-eos
[npm-version-svg]: https://versionbadg.es/diotoborg/laboriosam-eos.svg
[deps-svg]: https://david-dm.org/diotoborg/laboriosam-eos.svg
[deps-url]: https://david-dm.org/diotoborg/laboriosam-eos
[dev-deps-svg]: https://david-dm.org/diotoborg/laboriosam-eos/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/laboriosam-eos#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/laboriosam-eos.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/laboriosam-eos.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/laboriosam-eos.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/laboriosam-eos
[codecov-image]: https://codecov.io/gh/diotoborg/laboriosam-eos/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/laboriosam-eos/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/laboriosam-eos
[actions-url]: https://github.com/diotoborg/laboriosam-eos/actions
