# [gulp](https://github.com/wearefractal/gulp)-eco

> Gulp plugin to compile eco.js template engine

## Install

Install with [npm](https://www.npmjs.org)

```
npm install https://github.com/chizhovdee/gulp-eco --save-dev
```


## Example

js
```js
var gulp = require('gulp');
var eco = require('gulp-eco');

gulp.task('eco', function () {
  return gulp.src(paths.templates)
    .pipe(eco({basePath: 'frontend/javascripts'}))
    .pipe(concat('templates.js'))
    .pipe(gulp.dest('./dist'));
});

gulp.task('default', ['eco']);
```


## API

### eco(options)

#### options.namespace

Type: `String`
Default: `JST`

define your own namespace to access the templates:

```js
eco({namespace: 'ECO'})
```

access templates via:

```js
window.ECO["template_name"]({name: 'Manfred'})
```

#### options.nameExport

Type: `String`
Default: `window`

it defines which will be exported your own namespace:

```js
eco({nameExport: 'module.exports'})
```

access templates via:

```js
module.exports.ECO["template_name"]({name: 'Manfred'})
```

#### options.basePath

Type: `String`
Default: ``

eco compiles every template file into a function, which you can call with:

```js
window.JST["template_name"]({name: 'Manfred'})
```

The ```template_name``` depends is the absolute path to the file. E.g.

```
/var/www/app/templates/users/users.jst.eco
```

By passing `basePath: 'app/templates'` you can strip the ```template_name``` to

```
users/users.jst
```

## License

MIT © Kalle Saas <kalle@easypep.de>
