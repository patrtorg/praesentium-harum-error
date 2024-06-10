# @patrtorg/praesentium-harum-error <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

`Array.prototype.concat`, but made safe by ignoring Symbol.isConcatSpreadable

## Getting started

```sh
npm install --save @patrtorg/praesentium-harum-error
```

## Usage/Examples

```js
var safeConcat = require('@patrtorg/praesentium-harum-error');
var assert = require('assert');

assert.deepEqual([].concat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'arrays spread as expected with normal concat');
assert.deepEqual(safeConcat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'arrays spread as expected with safe concat');

String.prototype[Symbol.isConcatSpreadable] = true;
assert.deepEqual([].concat('foo', Object('bar')), ['foo', 'b', 'a', 'r'], 'spreadable String objects are spread with normal concat!!!');
assert.deepEqual(safeConcat('foo', Object('bar')), ['foo', Object('bar')], 'spreadable String objects are not spread with safe concat');

Array.prototype[Symbol.isConcatSpreadable] = false;
assert.deepEqual([].concat([1, 2], 3, [[4]]), [[], [1, 2], 3, [[4]]], 'non-concat-spreadable arrays do not spread with normal concat!!!');
assert.deepEqual(safeConcat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'non-concat-spreadable arrays still spread with safe concat');
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@patrtorg/praesentium-harum-error
[npm-version-svg]: https://versionbadg.es/ljharb/@patrtorg/praesentium-harum-error.svg
[deps-svg]: https://david-dm.org/ljharb/@patrtorg/praesentium-harum-error.svg
[deps-url]: https://david-dm.org/ljharb/@patrtorg/praesentium-harum-error
[dev-deps-svg]: https://david-dm.org/ljharb/@patrtorg/praesentium-harum-error/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@patrtorg/praesentium-harum-error#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@patrtorg/praesentium-harum-error.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@patrtorg/praesentium-harum-error.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@patrtorg/praesentium-harum-error.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@patrtorg/praesentium-harum-error
[codecov-image]: https://codecov.io/gh/ljharb/@patrtorg/praesentium-harum-error/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@patrtorg/praesentium-harum-error/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@patrtorg/praesentium-harum-error
[actions-url]: https://github.com/patrtorg/praesentium-harum-error/actions
