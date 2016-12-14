# rollup-plugin-jsx-js [![Build Status](https://travis-ci.org/lukeed/rollup-plugin-jsx-js.svg?branch=master)](https://travis-ci.org/lukeed/rollup-plugin-jsx-js)

> [JSX.js](https://github.com/thysultan/jsx.js) wrapper for Rollup


## Install

```
$ npm install --save-dev rollup-plugin-jsx-js
```


## Usage

```js
import jsx from 'rollup-plugin-jsx-js';

export default {
  dest: 'build/app.js',
  entry: 'src/index.js',
  sourceMap: true,
  plugins: [
    jsx({precise: true})
  ]
};
```


## Options

#### precise

Type: `boolean`<br>
Default: `false`

Should the source-mapping be precise?

Precise mappings map every single character, which allows your devtools to trace & pinpoint everything's exact location.
With less precise mappings, devtools may only be able to identify the correct line. However, they're quicker to generate and less bulky.


## Advanced Options

In addition to [`precise`](#precise), you may want to define [custom mappings](https://github.com/thysultan/jsx.js#api) for fuller control of your compiled JSX output.

The following functions are available to you: `text`, `element`, `component`, `props`, and `stringify`.

```js
// rollup.config.js
import jsx from 'rollup-plugin-jsx-js';

export default {
  entry: '...',
  plugins: [
    jsx({
      precise: true,
      text: children => ({...}),
      element: (type, props, children) => (...),
      component: (type, props, children) => ({...}),
      props: (key, value, props, node) => ({...}),
      stringify: (type, props, children, nodeType) => ({...})
    })
  ]
}
```


## License

MIT © [Luke Edwards](https://lukeed.com)
