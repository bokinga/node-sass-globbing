# node-sass-globbing

[![Build Status](https://travis-ci.org/nicobot/node-sass-globbing.svg?branch=master)](https://travis-ci.org/nicobot/node-sass-globbing)
[![Dependency Status](https://david-dm.org/nicobot/node-sass-globbing.svg)](https://david-dm.org/nicobot/node-sass-globbing)
[![npm](https://img.shields.io/npm/v/npm.svg)](https://www.npmjs.com/package/node-sass-globbing)

Allows you to use glob syntax in imports (i.e. `@import "dir/*.sass"`). Use as a custom importer for node-sass.

### Example

##### gulpfile.js
````
var nodeSassGlobbing = require('node-sass-globbing');

gulp.task('sass', function () {
	return gulp.src('styles/**/*.{scss,sass}')
			.pipe(sass({importer: nodeSassGlobbing}).on('error', sass.logError)))
			.pipe(gulp.dest('css'))			
}));
	
````

Then you can import globs!

##### foo.sass
````
@import "variables/**/*.scss"
@import "mixins/**/*.scss"
````

It also works with sourcemaps:
````
var nodeSassGlobbing = require('node-sass-globbing'),
	sourcemaps = require('gulp-sourcemaps');

gulp.task('sass', function () {
	return gulp.src('styles/**/*.{scss,sass}')
			.pipe(sourcemaps.init())
			.pipe(sass({importer: nodeSassGlobbing}).on('error', sass.logError)))
			.pipe(sourcemaps.write('./maps'))
			.pipe(gulp.dest('css'))			
}));

````


### Tests

````
npm test
````

### License
Available under the [MIT License](LICENSE.md).
