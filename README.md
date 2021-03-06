
# level-fs-browser

[level-fs](https://github.com/juliangruber/level-fs) as drop-in
[fs](nodejs.org/api/fs.html) replacement for the browser, to be used
with [browserify](https://github.com/substack/node-browserify).

## Usage

With this file, stored as `test.js`:

```js
var fs = require('fs');

fs.readFile('foo', function () {
  console.log(arguments);
});
```

you can bundle it up to use `level-fs` instead of `fs`, either using
browserify's api:

```js
var browserify = require('browserify');
var fs = require('fs');

var b = browserify();
b.require('level-fs-browser', { expose: 'fs' });
b.add(__dirname + '/test.js');
b.bundle().pipe(process.stdout);
```

or browserify's cli:

```bash
$ browserify -r fs:level-fs-browser test.js
```

**level-fs-browser** will (create and) use a database called `level-fs`.

## Installation

With [npm](http://npmjs.org) do

```bash
$ npm install level-fs-browser
```

## License

Copyright (c) 2013 Julian Gruber &lt;julian@juliangruber.com&gt;

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
