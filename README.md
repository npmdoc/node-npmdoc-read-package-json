# api documentation for  [read-package-json (v2.0.5)](https://github.com/npm/read-package-json#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-read-package-json.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-read-package-json) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-read-package-json.svg)](https://travis-ci.org/npmdoc/node-npmdoc-read-package-json)
#### The thing npm uses to read package.json files with semantics and defaults and validation

[![NPM](https://nodei.co/npm/read-package-json.png?downloads=true)](https://www.npmjs.com/package/read-package-json)

[![apidoc](https://npmdoc.github.io/node-npmdoc-read-package-json/build/screenCapture.buildNpmdoc.browser.%2Fhome%2Ftravis%2Fbuild%2Fnpmdoc%2Fnode-npmdoc-read-package-json%2Ftmp%2Fbuild%2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-read-package-json/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-read-package-json/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-read-package-json/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Isaac Z. Schlueter",
        "email": "i@izs.me",
        "url": "http://blog.izs.me/"
    },
    "bugs": {
        "url": "https://github.com/npm/read-package-json/issues"
    },
    "dependencies": {
        "glob": "^7.1.1",
        "graceful-fs": "^4.1.2",
        "json-parse-helpfulerror": "^1.0.2",
        "normalize-package-data": "^2.0.0"
    },
    "description": "The thing npm uses to read package.json files with semantics and defaults and validation",
    "devDependencies": {
        "standard": "^9.0.1",
        "tap": "^10.3.0"
    },
    "directories": {},
    "dist": {
        "shasum": "f93a64e641529df68a08c64de46389e8a3f88845",
        "tarball": "https://registry.npmjs.org/read-package-json/-/read-package-json-2.0.5.tgz"
    },
    "gitHead": "0b03bd75bda0540de4102b543b94ccaf3fb7c034",
    "homepage": "https://github.com/npm/read-package-json#readme",
    "license": "ISC",
    "main": "read-json.js",
    "maintainers": [
        {
            "name": "iarna",
            "email": "me@re-becca.org"
        },
        {
            "name": "isaacs",
            "email": "isaacs@npmjs.com"
        },
        {
            "name": "othiym23",
            "email": "ogd@aoaioxxysz.net"
        },
        {
            "name": "zkat",
            "email": "kat@sykosomatic.org"
        }
    ],
    "name": "read-package-json",
    "optionalDependencies": {
        "graceful-fs": "^4.1.2"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/npm/read-package-json.git"
    },
    "scripts": {
        "test": "standard && tap -J test/*.js"
    },
    "version": "2.0.5"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module read-package-json](#apidoc.module.read-package-json)
1.  [function <span class="apidocSignatureSpan">read-package-json.</span>extras (file, data, log_, strict_, cb_)](#apidoc.element.read-package-json.extras)
1.  object <span class="apidocSignatureSpan">read-package-json.</span>extraSet

#### [module read-package-json.extraSet](#apidoc.module.read-package-json.extraSet)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>0 (file, data, cb)](#apidoc.element.read-package-json.extraSet.0)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>1 (file, data, cb)](#apidoc.element.read-package-json.extraSet.1)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>2 (file, data, cb)](#apidoc.element.read-package-json.extraSet.2)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>3 (file, data, cb)](#apidoc.element.read-package-json.extraSet.3)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>4 (file, data, cb)](#apidoc.element.read-package-json.extraSet.4)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>5 (file, data, cb)](#apidoc.element.read-package-json.extraSet.5)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>6 (file, data, cb)](#apidoc.element.read-package-json.extraSet.6)
1.  [function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>7 (file, data, cb)](#apidoc.element.read-package-json.extraSet.7)



# <a name="apidoc.module.read-package-json"></a>[module read-package-json](#apidoc.module.read-package-json)

#### <a name="apidoc.element.read-package-json.extras"></a>[function <span class="apidocSignatureSpan">read-package-json.</span>extras (file, data, log_, strict_, cb_)](#apidoc.element.read-package-json.extras)
- description and source-code
```javascript
function extras(file, data, log_, strict_, cb_) {
  var log, strict, cb
  for (var i = 2; i < arguments.length - 1; i++) {
    if (typeof arguments[i] === 'boolean') {
      strict = arguments[i]
    } else if (typeof arguments[i] === 'function') {
      log = arguments[i]
    }
  }

  if (!log) log = function () {}
  cb = arguments[i]

  var set = readJson.extraSet
  var n = set.length
  var errState = null
  set.forEach(function (fn) {
    fn(file, data, then)
  })

  function then (er) {
    if (errState) return
    if (er) return cb(errState = er)
    if (--n > 0) return
    final(file, data, log, strict, cb)
  }
}
```
- example usage
```shell
...

By default this is a reference to the 'npmlog' module.  But if that
module can't be found, then it'll be set to just a dummy thing that does
nothing.

Replace with your own '{log,warn,error}' object for fun loggy time.

## readJson.extras(file, data, cb)

Run all the extra stuff relative to the file, with the parsed data.

Modifies the data as it does stuff.  Calls the cb when it's done.

## readJson.extraSet = [fn, fn, ...]
...
```



# <a name="apidoc.module.read-package-json.extraSet"></a>[module read-package-json.extraSet](#apidoc.module.read-package-json.extraSet)

#### <a name="apidoc.element.read-package-json.extraSet.0"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>0 (file, data, cb)](#apidoc.element.read-package-json.extraSet.0)
- description and source-code
```javascript
function gypfile(file, data, cb) {
  var dir = path.dirname(file)
  var s = data.scripts || {}
  if (s.install || s.preinstall) return cb(null, data)

  glob('*.gyp', { cwd: dir }, function (er, files) {
    if (er) return cb(er)
    gypfile_(file, data, files, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.1"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>1 (file, data, cb)](#apidoc.element.read-package-json.extraSet.1)
- description and source-code
```javascript
function serverjs(file, data, cb) {
  var dir = path.dirname(file)
  var s = data.scripts || {}
  if (s.start) return cb(null, data)
  glob('server.js', { cwd: dir }, function (er, files) {
    if (er) return cb(er)
    serverjs_(file, data, files, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.2"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>2 (file, data, cb)](#apidoc.element.read-package-json.extraSet.2)
- description and source-code
```javascript
function scriptpath(file, data, cb) {
  if (!data.scripts) return cb(null, data)
  var k = Object.keys(data.scripts)
  k.forEach(scriptpath_, data.scripts)
  cb(null, data)
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.3"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>3 (file, data, cb)](#apidoc.element.read-package-json.extraSet.3)
- description and source-code
```javascript
function authors(file, data, cb) {
  if (data.contributors) return cb(null, data)
  var af = path.resolve(path.dirname(file), 'AUTHORS')
  fs.readFile(af, 'utf8', function (er, ad) {
    // ignore error.  just checking it.
    if (er) return cb(null, data)
    authors_(file, data, ad, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.4"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>4 (file, data, cb)](#apidoc.element.read-package-json.extraSet.4)
- description and source-code
```javascript
function readme(file, data, cb) {
  if (data.readme) return cb(null, data)
  var dir = path.dirname(file)
  var globOpts = { cwd: dir, nocase: true, mark: true }
  glob('{README,README.*}', globOpts, function (er, files) {
    if (er) return cb(er)
    // don't accept directories.
    files = files.filter(function (file) {
      return !file.match(/\/$/)
    })
    if (!files.length) return cb()
    var fn = preferMarkdownReadme(files)
    var rm = path.resolve(dir, fn)
    readme_(file, data, rm, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.5"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>5 (file, data, cb)](#apidoc.element.read-package-json.extraSet.5)
- description and source-code
```javascript
function mans(file, data, cb) {
  var m = data.directories && data.directories.man
  if (data.man || !m) return cb(null, data)
  m = path.resolve(path.dirname(file), m)
  glob('**/*.[0-9]', { cwd: m }, function (er, mans) {
    if (er) return cb(er)
    mans_(file, data, mans, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.6"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>6 (file, data, cb)](#apidoc.element.read-package-json.extraSet.6)
- description and source-code
```javascript
function bins(file, data, cb) {
  if (Array.isArray(data.bin)) return bins_(file, data, data.bin, cb)

  var m = data.directories && data.directories.bin
  if (data.bin || !m) return cb(null, data)

  m = path.resolve(path.dirname(file), m)
  glob('**', { cwd: m }, function (er, bins) {
    if (er) return cb(er)
    bins_(file, data, bins, cb)
  })
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.read-package-json.extraSet.7"></a>[function <span class="apidocSignatureSpan">read-package-json.extraSet.</span>7 (file, data, cb)](#apidoc.element.read-package-json.extraSet.7)
- description and source-code
```javascript
function githead(file, data, cb) {
  if (data.gitHead) return cb(null, data)
  var dir = path.dirname(file)
  var head = path.resolve(dir, '.git/HEAD')
  fs.readFile(head, 'utf8', function (er, head) {
    if (er) return cb(null, data)
    githead_(file, data, dir, head, cb)
  })
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
