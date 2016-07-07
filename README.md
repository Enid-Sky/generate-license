# generate-license [![NPM version](https://img.shields.io/npm/v/generate-license.svg?style=flat)](https://www.npmjs.com/package/generate-license) [![NPM downloads](https://img.shields.io/npm/dm/generate-license.svg?style=flat)](https://npmjs.org/package/generate-license) [![Build Status](https://img.shields.io/travis/generate/generate-license.svg?style=flat)](https://travis-ci.org/generate/generate-license)

Generate a license file for a GitHub project.

## TOC

- [What is "Generate"?](#what-is-generate)
- [Command line usage](#command-line-usage)
  * [Install globally](#install-globally)
  * [Running generate-license](#running-generate-license)
  * [Running tasks](#running-tasks)
- [Available tasks](#available-tasks)
- [API usage](#api-usage)
  * [Install locally](#install-locally)
  * [Register as a plugin](#register-as-a-plugin)
  * [Run tasks](#run-tasks)
- [Customization](#customization)
  * [Destination directory](#destination-directory)
  * [Overriding templates](#overriding-templates)
- [About](#about)
  * [Related projects](#related-projects)
  * [Contributing](#contributing)
  * [Running tests](#running-tests)
  * [Author](#author)
  * [License](#license)

_(TOC generated by [verb](https://github.com/verbose/verb) using [markdown-toc](https://github.com/jonschlinkert/markdown-toc))_

![generate-license demo](https://raw.githubusercontent.com/generate/generate-license/master/demo.gif)

## What is "Generate"?

Generate is a command line tool and developer framework for scaffolding out new GitHub projects using [generators](https://github.com/generate/generate/blob/master/docs/generators.md) and[tasks](https://github.com/generate/generate/blob/master/docs/tasks.md) . Answers to prompts and the user's environment can be used to determine the templates, directories, files and contents to build. Support for[gulp](http://gulpjs.com), [base](https://github.com/node-base/base) and [assemble](https://github.com/assemble/assemble) plugins, and much more.

For more information about Generate:

* Visit the [generate project](https://github.com/generate/generate)
* Visit the [generate documentation](https://github.com/generate/generate/blob/master/docs/)
* Find [generators on npm](https://www.npmjs.com/browse/keyword/generate-generator) (help us [author generators](https://github.com/generate/generate/blob/master/docs/micro-generators.md) )

## Command line usage

### Install globally

**Installing the CLI**

To run the `license` generator from the command line, you'll need to install [generate](https://github.com/generate/generate) globally first. You can do that now with the following command:

```sh
$ npm install --global generate
```

This adds the `gen` command to your system path, allowing it to be run from any directory.

**Install generate-license**

You may now install this module with the following command:

```sh
$ npm install --global generate-license
```

### Running generate-license

You should now be able to run `generate-license` with the following command:

```js
$ gen license
```

**What will happen?**

Running `$ gen license` will run the generator's [default task](#licensedefault), which creates a new `LICENSE` file in the current working directory.

### Running tasks

Tasks on `generate-license` are by run passing the name of the task to run after the generator name, delimited by a comma:

```sh
$ gen license:foo
       ^       ^
generator     task
```

**Example**

The following will run generator `foo`, task `bar`:

```sh
$ gen foo:bar
```

**Default task**

If a task is not explicitly passed Generate's CLI will run the `default` task.

## Available tasks

Visit Generate's [documentation for tasks](https://github.com/generate/generate/blob/master/docs/tasks.md).

## API usage

Use `generate-license` as a [plugin](https://github.com/generate/generate/blob/master/docs/plugins.md) in your own[generator](https://github.com/generate/generate/blob/master/docs/generators.md) .

### Install locally

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save generate-license
```

### Register as a plugin

Inside your own [generator](https://github.com/generate/generate/blob/master/docs/generators.md) :

```js
module.exports = function(app) {
  // register generate-license as a plugin
  app.use(require('generate-license'));
};
```

### Run tasks

Programmatically run tasks from `generate-license`:

```js
module.exports = function(app) {
  // register generate-license as a plugin
  app.use(require('generate-license'));

  // run the `default` task on generate-license
  app.task('foo', function(cb) {
    app.generate('generate-license', cb);
  });

  // or run a specific task on generate-license 
  // (where `foo` is the name of the task to run)
  app.task('bar', function(cb) {
    app.generate('generate-license:foo', cb);
  });
};
```

Visit the [generator docs](https://github.com/generate/generate/blob/master/docs/generators.md) to learn more about creating, installing, using and publishing generators.

## Customization

### Destination directory

To customize the destination directory, install [generate-dest](https://github.com/generate/generate-dest) globally, then in the command line prefix `dest` before any other generator names.

For example, the following will prompt you for the destination path to use, then pass the result to `generate-license`:

```sh
$ gen dest license
```

### Overriding templates

You can override a template by adding a template of the same name to the `templates` directory in user home.

For example, to override the `LICENSE` template, add a template at the following path `~/generate/generate-license/templates/LICENSE`, where `~/` is the user-home directory that `os.homedir()` resolves  on your system.

## About

### Related projects

You might also be interested in these projects:

* [generate-eslint](https://www.npmjs.com/package/generate-eslint): Generate a `.eslintrc.json` or `.eslintignore` file as part of a larger build workflow. This generator… [more](https://github.com/generate/generate-eslint) | [homepage](https://github.com/generate/generate-eslint "Generate a `.eslintrc.json` or `.eslintignore` file as part of a larger build workflow. This generator can be used as a sub-generator or plugin inside other generators.")
* [generate-install](https://www.npmjs.com/package/generate-install): Generator that automatically detects the dependencies or devDependencies to install based on the templates or… [more](https://github.com/generate/generate-install) | [homepage](https://github.com/generate/generate-install "Generator that automatically detects the dependencies or devDependencies to install based on the templates or includes used. This can be used as a sub-generator or plugin in your own generator.")
* [generate-package](https://www.npmjs.com/package/generate-package): Generate a package.json for a project. This generator can be used as a plugin or… [more](https://github.com/generate/generate-package) | [homepage](https://github.com/generate/generate-package "Generate a package.json for a project. This generator can be used as a plugin or sub-generator in your own generator, as a component of a larger build workflow.")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

### Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

### License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/generate/generate-license/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on July 07, 2016._