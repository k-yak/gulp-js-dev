# [gulp](https://github.com/wearefractal/gulp)-js-dev

> Toggle js comments so that you can enable functionality for dev vs.
> production.

**Turn this:**
```js
var server = '';
/* !dev */
server = 'http://server.prod';
/* /!dev */
/* dev */
server = 'http://server.dev';
/* /dev */
```

**Into this for development**

```js
var server = '';
/* !dev */
/*
server = 'http://server.prod';
*/
/* /!dev */
/* dev */
server = 'http://server.dev';
/* /dev */
```

**Or into this for production**

```js
var server = '';
/* !dev */
server = 'http://server.prod';
/* /!dev */
/* dev */
/*
server = 'http://server.dev';
*/
/* /dev */
```

## Example Usage with Gulp

**Development Task**
```js
var gulp = require('gulp');
var dev = require('gulp-js-dev');

gulp.task('dev', function() {
  gulp.src('main.js')
      .pipe(dev(true))
      .pipe(gulp.dest('main.js'));
});
```
**Default Task (for prod)**
```js
var gulp = require('gulp');
var dev = require('gulp-dev');

gulp.task('prod', function() {
  gulp.src('main.js')
      .pipe(dev(false))
      .pipe(gulp.dest('public/main.js'));
});
```

## API

### dev(inDevelopmentMode)

`inDevelopmentMode` is a boolean value that helps us decide what to keep
and what to remove.

## License

Copyright (c) 2014 Ryan Olson <ryan.olson.x@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
