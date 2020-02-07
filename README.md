# metalsmith-html-glob

[![](https://badgen.net/npm/v/metalsmith-html-glob?icon=npm)](https://www.npmjs.com/package/metalsmith-html-glob)
[![Known Vulnerabilities](https://snyk.io/test/npm/metalsmith-html-glob/badge.svg)](https://snyk.io/test/npm/metalsmith-html-glob)
[![](https://badgen.net/npm/dw/metalsmith-html-glob)](https://www.npmjs.com/package/metalsmith-html-glob)

[![](https://badgen.net/badge/emmercm/metalsmith-html-glob/purple?icon=github)](https://github.com/emmercm/metalsmith-html-glob)
[![](https://badgen.net/codecov/c/github/emmercm/metalsmith-html-glob/master?icon=codecov)](https://codecov.io/gh/emmercm/metalsmith-html-glob)
[![](https://badgen.net/github/license/emmercm/metalsmith-html-glob?color=grey)](https://github.com/emmercm/metalsmith-html-glob/blob/master/LICENSE)

A Metalsmith plugin to apply glob patterns within HTML.

## Installation

```bash
npm install --save metalsmith-html-glob
```

## JavaScript Usage

```javascript
const Metalsmith = require('metalsmith');
const glob       = require('metalsmith-html-glob');

Metalsmith(__dirname)
    .use(glob({
        // options here
    }))
```

## Options

### Default Options

```json
{
    "html": "**/*.html",
    "tags": {
        "a": "href",
        "img": "src",
        "link": "href",
        "script": "src"
    }
}
```

### `html`

`string` - [minimatch](https://www.npmjs.com/package/minimatch) glob pattern for HTML files.

### `tags`

`Object` - what tags and attributes to glob:

```json
{
    "tags": {
        "a": "href",
        "img": "src",
        "link": "href",
        "script": "src"
    }
}
```

## Example HTML

### Example Input

Given a file tree:

```
/
|-- static/
|   |-- css/
|   |   |-- bootstrap.min.css
|   |-- js/
|   |   |-- bootstrap.bundle.min.js
|-- index.html
```

And `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <link rel="stylesheet" href="**/*.css">
    </head>
    <body>
        <script src="**/*.js"></script>
    </body>
</html>
```

### Example Output

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <link rel="stylesheet" href="static/css/bootstrap.min.css">
    </head>
    <body>
        <script src="static/js/bootstrap.bundle.min.js"></script>
    </body>
</html>
```

## Changelog

[Changelog](./CHANGELOG.md)
