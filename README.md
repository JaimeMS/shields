# GitHub badges in SVG format

[![npm version](http://b.adge.me/npm/v/gh-badges.svg)](https://npmjs.org/package/gh-badges)
![coverage](https://rawgithub.com/badges/gh-badges/master/coverage.svg)

Make your own badges [here][badges]!

[badges]: <http://b.adge.me>

# Install the API

```bash
npm install gh-badges
```

```js
var badge = require('gh-badges');
badge({ text: [ "build", "passed" ], "colorscheme": "green" },
  function(svg) {
    // svg is a String… of your badge.
  });
```

# Use the CLI

```bash
npm install -g gh-badges
badge build passed :green .png > mybadge.png
# Stored a PNG version of your badge on disk.
```

# Set the Server

```bash
git clone git@github.com:badges/gh-badges
cd gh-badges
npm install
sudo npm start
```

# Format

The format is the following:

```js
{
  /* Textual information shown, in order. */
  "text": [ "build", "passed" ],
  "colorscheme": "green"
  /* … Or… */
  "colorA": "#555",
  "colorB": "#4c1"
}
```

# Defaults

If you want to add a default badge, you only need to modify
`default-badges.json`. The format is the same as that given to the API.

If you want to add a colorscheme, head to `colorscheme.json`. Each scheme has a
name and a [CSS/SVG color][] for the color used in the first box (for the first
piece of text, field `colorA`) and for the one used in the second box (field
`colorB`).

[CSS/SVG color]: http://www.w3.org/TR/SVG/types.html#DataTypeColor

```js
"green": {
  "colorB": "#4c1"
}
```

Both `colorA` and `colorB` have default values. Usually, the first box uses the
same dark grey, so you can rely on that default value by not providing a
`"colorA"` field (such as above).

You can also use the `"colorA"` and `"colorB"` fields directly in the badges if
you don't want to make a color scheme for it. In that case, remove the
`"colorscheme"` field altogether.

# Requirements

Because of the usage of the npm module [canvas][canvas-pkg] *you need* to have
**cairo** installed.

For more information check the [wiki][canvas-wiki] of the canvas project with
system-specific installation details.

[canvas-pkg]: https://npmjs.org/package/canvas
[canvas-wiki]: https://github.com/LearnBoost/node-canvas/wiki/_pages

# Making your Heroku badge server

Once you have installed the [Heroku Toolbelt][]:

[Heroku Toolbelt]: (https://toolbelt.heroku.com/):

```bash
heroku login
heroku create your-app-name
heroku config:set BUILDPACK_URL=https://github.com/mojodna/heroku-buildpack-multi.git#build-env
cp /path/to/Verdana.ttf .
make deploy
heroku open
```

# Origin

See <https://github.com/h5bp/lazyweb-requests/issues/150>.

# License

All work here is licensed CC0.
