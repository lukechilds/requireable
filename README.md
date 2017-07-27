# requireable

> Enables a module to require itself by name

[![Build Status](https://travis-ci.org/lukechilds/requireable.svg?branch=master)](https://travis-ci.org/lukechilds/requireable)
[![Coverage Status](https://coveralls.io/repos/github/lukechilds/requireable/badge.svg?branch=master)](https://coveralls.io/github/lukechilds/requireable?branch=master)
[![npm](https://img.shields.io/npm/v/requireable.svg)](https://www.npmjs.com/package/requireable)

Mocks the require command to include the current package when the `name` from the current `package.json` is required.

Uses `process.cwd()` to find the current `package.json` so this is only meant to be used in scripts executed from the CLI. This will not work on a published package!

## Install

```shell
npm install --save-dev requireable
```

## Usage

```js
require('requirable');
// That's it! `require` has now been patched

const myPackage = require('package-name')
```

## AVA Usage

Some tests runners such as [AVA](https://github.com/avajs/ava) can require packages automatically for you. If you're using AVA add the following to your package.json:

```json
"ava": {
  "require": [
    "requireable"
  ]
},
 ```

 You can now `require` (or `import`) your package in your AVA tests by name.

 e.g instead of:

 ```js
 import test from 'ava';
 import myPackage from '../';
 ```

 You can now do:

 ```js
 import test from 'ava';
 import myPackage from 'package-name';
 ```

## API

### require('requireable')

Patches the require function to be able to require the current module by name.

Returns an object.

#### obj.success

Type: `boolean`

True or false depending on whether we could find `package.json`.

#### obj.path

Type: `undefined`, `string`

Path to the folder containing `package.json`.

#### obj.name

Type: `undefined`, `string`

Name of the module in `package.json`.

## License

MIT © Luke Childs
