[uRequire](http://urequire.org) [ResourceConverter](http://urequire.org/resourceconverters.coffee) that injects a `var VERSION = ''` where its needed: before the body of the 'main' module of your bundle (or any other module).

# Usage

* Add 'urequire-rc-inject-version' to your `package.json` / `node_modules` (i.e `npm install urequire-rc-inject-version --save`).

* add 'inject-version' to your `bundle.resources`, eg :

```
  resources: [
    ...
    'inject-version'
    ...
   ]

```

By default:

 * it reads the `version` of your project's `package.json`.

 * It adds it before the body of the 'main' module, if `bundle.main` is defined (otherwise it fails, unless `options.modules` is passed).

To override these defaults use it as `['inject-version', options]` where options is a `{}` like this:

```
    [ 'inject-version', {
        VERSION: pkg.version + '-NIGHTLY',
        modules: 'my/module/path/**/*'
       }
    ]
```

The `modules` can be a `String` or an `Array` of module paths (always relative to `bundle.path`, without `.js`) that filters module paths using [`is_file_in`](https://github.com/Unity-Billal-mesloub/is_file_in) which is minimatch on steroids.

For example:

```
    [ 'inject-version', {
        VERSION: pkg.version + '-NIGHTLY',
        modules: ['models/**/*', '!models/aliens/**/*', /integration/]
       }
    ]
```

### See more ResourceConverter usage / configuring examples

http://github.com/Unity-Billal-mesloub/urequire-rc-less/

http://urequire.org


