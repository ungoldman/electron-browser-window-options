# electron-browser-window-options

[![npm][npm-image]][npm-url]
[![travis][travis-image]][travis-url]
[![standard][standard-image]][standard-url]

[npm-image]: https://img.shields.io/npm/v/electron-browser-window-options.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/electron-browser-window-options
[travis-image]: https://img.shields.io/travis/ngoldman/electron-browser-window-options.svg?style=flat-square
[travis-url]: https://travis-ci.org/ngoldman/electron-browser-window-options
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[standard-url]: http://npm.im/standard

Reference for default [Electron BrowserWindow options](https://github.com/atom/electron/blob/master/docs/api/browser-window.md).

Can be used just for reference and copy pasting, or can be imported and used for, like, whatever:

* require and override to make your own defaults
* clone and export opts for different window types
* ...
* profit

**Why?**

Having a portable javascript object with defaults was handier for me than the markdown version in the docs.

## Install

```
npm install electron-browser-window-options
```

## Usage

```js
const electron = require('electron')
const defaultWindowOpts = require('electron-browser-window-options')
const app = electron.app
const BrowserWindow = electron.BrowserWindow
let mainWindow = null

// clone defaults and customize options
const myOpts = Object.assign({}, defaultWindowOpts, {
  titleBarStyle: 'hidden'
})

app.on('ready', function () {
  mainWindow = new BrowserWindow(myOpts)
})
```

Note that using defaults as-is amounts to the same as creating a new `BrowserWindow` with no options, so it serves no purposes. This module is only useful if you want to import and modify a plain javascript object.

## Contributing

Exported options should mirror [Electron BrowserWindow documentation](https://github.com/atom/electron/blob/master/docs/api/browser-window.md) exactly. If something is out of date, please feel free to make an issue or send a pull request.

## License

[CC0](LICENSE)
