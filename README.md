# electron-browser-window-options

[![npm][1]][2]
[![travis][3]][4]
[![standard][5]][6]
[![downloads][7]][2]

[1]: https://img.shields.io/npm/v/electron-browser-window-options.svg?style=flat-square
[2]: https://www.npmjs.com/package/electron-browser-window-options
[3]: https://img.shields.io/travis/ungoldman/electron-browser-window-options/master.svg?style=flat-square
[4]: https://travis-ci.org/ungoldman/electron-browser-window-options
[5]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[6]: http://standardjs.com/
[7]: https://img.shields.io/npm/dm/electron-browser-window-options.svg?style=flat-square

Reference for default [Electron BrowserWindow options][docs].

---

⚠️ NO LONGER MAINTAINED ⚠️

---

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
var electron = require('electron')
var defaultWindowOpts = require('electron-browser-window-options')
var app = electron.app
var BrowserWindow = electron.BrowserWindow
var mainWindow = null

// clone defaults and customize options
var myOpts = Object.assign({}, defaultWindowOpts, {
  titleBarStyle: 'hidden'
})

app.on('ready', function () {
  mainWindow = new BrowserWindow(myOpts)
})
```

Note that using defaults as-is amounts to the same as creating a new `BrowserWindow` with no options, so it serves no purposes. This module is only useful if you want to import and modify a plain javascript object.

## Reference

This is the contents of [index.js](index.js), hand edited and reformatted from the original [Electron BrowserWindow docs][docs], copied here for your viewing pleasure!

```js
module.exports = {

  // Integer - Window's width in pixels. Default is `800`.
  width: 800,

  // Integer - Window's height in pixels. Default is `600`.
  height: 600,

  // Integer - Window's left offset from screen. Default is to center the window.
  x: undefined,

  // Integer - Window's top offset from screen. Default is to center the window.
  y: undefined,

  // Boolean - The `width` and `height` would be used as web page's size, which means the actual window's size will include window frame's size and be slightly larger. Default is `false`.
  useContentSize: false,

  // Boolean - Show window in the center of the screen.
  center: undefined,

  // Integer - Window's minimum width. Default is `0`.
  minWidth: 0,

  // Integer - Window's minimum height. Default is `0`.
  minHeight: 0,

  // Integer - Window's maximum width. Default is no limit.
  maxWidth: undefined,

  // Integer - Window's maximum height. Default is no limit.
  maxHeight: undefined,

  // Boolean - Whether window is resizable. Default is `true`.
  resizable: true,

  // Boolean - Whether the window should always stay on top of other windows. Default is `false`.
  alwaysOnTop: false,

  // Boolean - Whether the window should show in fullscreen. When set to `false` the fullscreen button will be hidden or disabled on OS X. Default is `false`.
  fullscreen: false,

  // Boolean - Whether to show the window in taskbar. Default is `false`.
  skipTaskbar: false,

  // Boolean - The kiosk mode. Default is `false`.
  kiosk: false,

  // String - Default window title. Default is `'Electron'`.
  title: 'Electron',

  // [NativeImage](https://github.com/atom/electron/blob/master/docs/api/native-image.md) - The window icon, when omitted on Windows the executable's icon would be used as window icon.
  icon: undefined,

  // Boolean - Whether window should be shown when created. Default is `true`.
  show: true,

  // Boolean - Specify `false` to create a [Frameless Window](https://github.com/atom/electron/blob/master/docs/api/frameless-window.md). Default is `true`.
  frame: true,

  // Boolean - Whether the web view accepts a single mouse-down event that simultaneously activates the window. Default is `false`.
  acceptFirstMouse: false,

  // Boolean - Whether to hide cursor when typing. Default is `false`.
  disableAutoHideCursor: false,

  // Boolean - Auto hide the menu bar unless the `Alt` key is pressed. Default is `false`.
  autoHideMenuBar: false,

  // Boolean - Enable the window to be resized larger than screen. Default is `false`.
  enableLargerThanScreen: false,

  // String - Window's background color as Hexadecimal value, like `#66CD00` or `#FFF`. This is only implemented on Linux and Windows. Default is `#000` (black).
  backgroundColor: '#000',

  // Boolean - Forces using dark theme for the window, only works on some GTK+3 desktop environments. Default is `false`.
  darkTheme: false,

  // Boolean - Makes the window [transparent](https://github.com/atom/electron/blob/master/docs/api/frameless-window.md). Default is `false`.
  transparent: false,

  // String - Specifies the type of the window, which applies additional platform-specific properties. By default it's undefined and you'll get a regular app window. Supported values:
  // * On Linux, possible types are `desktop`, `dock`, `toolbar`, `splash`, `notification`.
  // * On OS X, possible types are `desktop`, `textured`. The `textured` type adds metal gradient appearance (`NSTexturedBackgroundWindowMask`). The `desktop` type places the window at the desktop background window level (`kCGDesktopWindowLevel - 1`). Note that desktop window will not receive focus, keyboard or mouse events, but you can use `globalShortcut` to receive input sparingly.
  type: undefined,

  // String, OS X - specifies the style of window title bar. This option is supported on OS X 10.10 Yosemite and newer. There are three possible values:
  // * `default` or not specified, results in the standard gray opaque Mac title bar.
  // * `hidden` results in a hidden title bar and a full size content window, yet the title bar still has the standard window controls ("traffic lights") in the top left.
  // * `hidden-inset` results in a hidden title bar with an alternative look where the traffic light buttons are slightly more inset from the window edge.
  titleBarStyle: undefined,

  // Object - Settings of web page's features.
  webPreferences: {

    // Boolean - Whether node integration is enabled. Default is `true`.
    nodeIntegration: true,

    // String - Specifies a script that will be loaded before other scripts run in the page. This script will always have access to node APIs no matter whether node integration is turned on or off. The value should be the absolute file path to the script.

    // When node integration is turned off, the preload script can reintroduce Node global symbols back to the global scope. See example [here](https://github.com/atom/electron/blob/master/docs/api/process.md#event-loaded).
    preload: undefined,

    // String - Sets the session used by the page. If `partition` starts with `persist:`, the page will use a persistent session available to all pages in the app with the same `partition`. if there is no `persist:` prefix, the page will use an in-memory session. By assigning the same `partition`, multiple pages can share the same session. If the `partition` is unset then default session of the app will be used.
    partition: undefined,

    // Number - The default zoom factor of the page, `3.0` represents `300%`. Default is `1.0`.
    zoomFactor: 1.0,

    // Boolean - Enables JavaScript support. Default is `true`.
    javascript: true,

    // Boolean - When setting `false`, it will disable the same-origin policy (Usually using testing websites by people), and set `allowDisplayingInsecureContent` and `allowRunningInsecureContent` to `true` if these two options are not set by user. Default is `true`.
    webSecurity: true,

    // Boolean - Allow an https page to display content like images from http URLs. Default is `false`.
    allowDisplayingInsecureContent: false,

    // Boolean - Allow a https page to run JavaScript, CSS or plugins from http URLs. Default is `false`.
    allowRunningInsecureContent: false,

    // Boolean - Enables image support. Default is `true`.
    images: true,

    // Boolean - Enables Java support. Default is `false`.
    java: false,

    // Boolean - Make TextArea elements resizable. Default is `true`.
    textAreasAreResizable: true,

    // Boolean - Enables WebGL support. Default is `true`.
    webgl: true,

    // Boolean - Enables WebAudio support. Default is `true`.
    webaudio: true,

    // Boolean - Whether plugins should be enabled. Default is `false`.
    plugins: false,

    // Boolean - Enables Chromium's experimental features. Default is `false`.
    experimentalFeatures: false,

    // Boolean - Enables Chromium's experimental canvas features. Default is `false`.
    experimentalCanvasFeatures: false,

    // Boolean - Enables overlay scrollbars. Default is `false`.
    overlayScrollbars: false,

    // Boolean - Enables overlay fullscreen video. Default is `false`.
    overlayFullscreenVideo: false,

    // Boolean - Enables Shared Worker support. Default is `false`.
    sharedWorker: false,

    // Boolean - Enables DirectWrite font rendering system on Windows. Default is `true`.
    directWrite: true,

    // Boolean - Page would be forced to be always in visible or hidden state once set, instead of reflecting current window's visibility. Users can set it to `true` to prevent throttling of DOM timers. Default is `false`.
    pageVisibility: false
  }
}
```

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) before getting started.

Exported options should mirror [Electron BrowserWindow documentation][docs] exactly. If something is out of date, please feel free to make an issue or send a pull request.

## License

[ISC](LICENSE.md)

[docs]: https://github.com/atom/electron/blob/master/docs/api/browser-window.md
