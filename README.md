# gulp-dotnet-watch

dotnet-watch plugin for [Gulp](https://github.com/gulpjs/gulp) (but, not really)

## Install

```
npm install gulp-dotnet-watch --save-dev
```

## Basic Usage

```javascript
var gulp = require('gulp'),
	DotnetWatch = require('gulp-dotnet-watch');

gulp.task('watch-server', function () {
	DotnetWatch.watch('run');
});
```

## Advanced Usage

```javascript
var gulp = require('gulp'),
	DotnetWatch = require('gulp-dotnet-watch');

gulp.task('watch-server', function () {
	var watcher = new DotnetWatch({
		project: './WebFull',
		verbose:, 'true'
		arguments: {
			framework: 'net451',
			customArg1: 'Custom Value 1'
		}
	});

	watcher.watch('run', function() {
		console.log('dotnet-watch has loaded.');
	}});
});
```

## Options

#### cwd

The `cwd` option is based through to the child process.

**Default:** './'

#### project

The project to be watched.

**Default:** null

#### quiet

Suppresses all output except warnings and errors.

**Default:** false

#### verbose

Show verbose output.

**Default:** false

#### options

Special value options that will be passed to the child dotnet process. For example `[ 'verbose', 'no-build' ]` woudl result in `-- --verbose --no-build`.

**Default:** null

#### arguments

Special key/value arguments that will be passed to the child process. For example `{ framework: 'net451', configuration: 'Debug', customArg1: 'Custom Value 1' }` would result in `-- --framework net451 --configuration Debug --customArg1 'Custom Value 1'`.

**Default:** null

## Methods

#### DotnetWatch.watch(task [, options [, loaded]])

This static method will start a watch process for the provided `task`, and can be configured by passing an `options` object. The method will return an active watcher instance, and the `loaded` callback will be issued once the watch process has started the application. Supported `task`s include 'run' and 'test', however others may still work.

#### new DotnetWatch([options]).watch(task [, loaded])

This method will start a watch process for the provided `task`. The method will return an active watcher instance, and the `loaded` callback will be issued once the watch process has started the application.

#### new DotnetWatch([options]).kill()

This method will kill the active watch process on the watcher instance.

## Properties

#### isWatching

This property is `true` when the application is ready to receive requests, otherwise `false`.

#### options

This property reveals the options that where used to configure the watcher.

## License

MIT
