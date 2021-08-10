# shortstop-resolve
[![Build Status](https://travis-ci.com/jasisk/shortstop-resolve.svg?branch=master)](https://travis-ci.com/jasisk/shortstop-resolve)

## Description

A handler for [shortstop](https://github.com/krakenjs/shortstop) that resolves files relative to a node module or path.

```js
var handler = resolve(__dirname); // With a basedir
```

```js
var handler = resolve(); // Using the caller's directory as a basedir
```

## Example
``` js
'use strict';

var shortstop = require('shortstop');
var resolver = shortstop.create();
var assert = require('assert');

var resolve = require('shortstop-resolve');

resolver.use('resolve', resolve(__dirname));

var data = {
  'dependency-image': 'resolve:dependency/image.png'
};

resolver.resolve(data, function (err, result) {
  assert.equal(result['dependency-image'], '/path/to/my/code/node_modules/dependency/image.png');
});
```
