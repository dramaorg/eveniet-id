# @dramaorg/eveniet-id <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.findLastIndex` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-array-find-from-last).

Because `Array.prototype.findLastIndex` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @dramaorg/eveniet-id
```

## Usage/Examples

```js
var findLastIndex = require('@dramaorg/eveniet-id');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var isNumber = function (x) { return typeof x === 'number' };

assert.deepEqual(findLastIndex(arr, isNumber), 3);
```

```js
var findLastIndex = require('@dramaorg/eveniet-id');
var assert = require('assert');
/* when Array#findLastIndex is not present */
delete Array.prototype.findLastIndex;
var shimmed = findLastIndex.shim();

assert.equal(shimmed, findLastIndex.getPolyfill());
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

```js
var findLastIndex = require('@dramaorg/eveniet-id');
var assert = require('assert');
/* when Array#findLastIndex is present */
var shimmed = findLastIndex.shim();

assert.equal(shimmed, Array.prototype.findLastIndex);
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@dramaorg/eveniet-id
[npm-version-svg]: https://versionbadg.es/dramaorg/eveniet-id.svg
[deps-svg]: https://david-dm.org/dramaorg/eveniet-id.svg
[deps-url]: https://david-dm.org/dramaorg/eveniet-id
[dev-deps-svg]: https://david-dm.org/dramaorg/eveniet-id/dev-status.svg
[dev-deps-url]: https://david-dm.org/dramaorg/eveniet-id#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@dramaorg/eveniet-id.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@dramaorg/eveniet-id.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@dramaorg/eveniet-id.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@dramaorg/eveniet-id
[codecov-image]: https://codecov.io/gh/dramaorg/eveniet-id/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/dramaorg/eveniet-id/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/dramaorg/eveniet-id
[actions-url]: https://github.com/dramaorg/eveniet-id
