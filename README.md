# @womorg/tempora-maxime-voluptates <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `String.prototype.at` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-item-method/).

Because `String.prototype.at` depends on a receiver (the `this` value), the main export takes the string to operate on as the first argument.

Note that versions of this package before v1.0.0 reflect an earlier, now-inactive proposal (https://github.com/mathiasbynens/String.prototype.at).

## Getting started

```sh
npm install --save @womorg/tempora-maxime-voluptates
```

## Usage/Examples

```js
var at = require('@womorg/tempora-maxime-voluptates');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = at(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var at = require('@womorg/tempora-maxime-voluptates');
var assert = require('assert');
/* when String#at is not present */
delete String.prototype.at;
var shimmedFlatMap = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, at.getPolyfill());
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

```js
var at = require('@womorg/tempora-maxime-voluptates');
var assert = require('assert');
/* when String#at is present */
var shimmedIncludes = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, String.prototype.at);
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@womorg/tempora-maxime-voluptates
[npm-version-svg]: https://versionbadg.es/womorg/tempora-maxime-voluptates.svg
[deps-svg]: https://david-dm.org/womorg/tempora-maxime-voluptates.svg
[deps-url]: https://david-dm.org/womorg/tempora-maxime-voluptates
[dev-deps-svg]: https://david-dm.org/womorg/tempora-maxime-voluptates/dev-status.svg
[dev-deps-url]: https://david-dm.org/womorg/tempora-maxime-voluptates#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@womorg/tempora-maxime-voluptates.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@womorg/tempora-maxime-voluptates.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@womorg/tempora-maxime-voluptates.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@womorg/tempora-maxime-voluptates
[codecov-image]: https://codecov.io/gh/womorg/tempora-maxime-voluptates/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/womorg/tempora-maxime-voluptates/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/womorg/tempora-maxime-voluptates
[actions-url]: https://github.com/womorg/tempora-maxime-voluptates/actions
