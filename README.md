[![Build Status](https://travis-ci.org/mapbox/makizushi.svg)](https://travis-ci.org/mapbox/makizushi)

# makizushi

Professional [Maki](https://www.mapbox.com/maki/) chef. This module produces custom markers based
on the Maki icon set, in custom sizes and colors. To do this, it chooses, tints, and flattens parts
of the image, using [node-blend](https://github.com/mapbox/node-blend).

## install

    npm install --save makizushi

## api

### `makizushi(options, callback)`

Options:

* `tint`: a color in rgb or rrggbb
* `symbol`: a maki symbol name, or a single char of `[a-z0-9]`
* `size`: one of `s`, `m`, or `l`
* `base`: `"pin"`

Callback: `(err, data)` in which err is an error if any, and data is a
buffer of image data.

## usage

```js
var makizushi = require('makizushi');

makizushi({
    base: 'pin',
    size: 'l',
    tint: '333',
    label: 'a'
}, function(err, buf) {
    if (err) throw err;
    fs.writeFileSync('marker.png', buf);
});
```
