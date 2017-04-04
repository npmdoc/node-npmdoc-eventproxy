# api documentation for  [eventproxy (v0.3.5)](https://github.com/JacksonTian/eventproxy)  [![npm package](https://img.shields.io/npm/v/npmdoc-eventproxy.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-eventproxy) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-eventproxy.svg)](https://travis-ci.org/npmdoc/node-npmdoc-eventproxy)
#### An implementation of task/event based asynchronous pattern.

[![NPM](https://nodei.co/npm/eventproxy.png?downloads=true)](https://www.npmjs.com/package/eventproxy)

[![apidoc](https://npmdoc.github.io/node-npmdoc-eventproxy/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-eventproxy_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-eventproxy/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-eventproxy/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-eventproxy/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jackson Tian",
        "email": "shyvo1987@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/JacksonTian/eventproxy/issues"
    },
    "contributors": [
        {
            "name": "Jackson Tian",
            "email": "shyvo1987@gmail.com"
        },
        {
            "name": "fengmk2",
            "email": "fengmk2@gmail.com"
        }
    ],
    "dependencies": {
        "debug": "2.2.0"
    },
    "description": "An implementation of task/event based asynchronous pattern.",
    "devDependencies": {
        "browser": "0.2.6",
        "contributors": "*",
        "growl": "1.9.2",
        "istanbul": "*",
        "mocha": "2.5.3",
        "pedding": "1.0.0"
    },
    "directories": {
        "test": "test"
    },
    "dist": {
        "shasum": "4db3290dcbc51cf067cbb6752e3c40b5d917212f",
        "tarball": "https://registry.npmjs.org/eventproxy/-/eventproxy-0.3.5.tgz"
    },
    "files": [
        "lib",
        "index.js"
    ],
    "gitHead": "410b8a2021be9e1ed6ae396483bfb2ebe34f223e",
    "homepage": "https://github.com/JacksonTian/eventproxy",
    "keywords": [
        "event",
        "task-base",
        "event machine",
        "nested callback terminator"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jacksontian",
            "email": "shyvo1987@gmail.com"
        }
    ],
    "name": "eventproxy",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/JacksonTian/eventproxy.git"
    },
    "scripts": {
        "test": "make test-all"
    },
    "spm": {
        "main": "index.js",
        "ignore": [
            "test"
        ]
    },
    "version": "0.3.5"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module eventproxy](#apidoc.module.eventproxy)
1.  [function <span class="apidocSignatureSpan">eventproxy.</span>EventProxy ()](#apidoc.element.eventproxy.EventProxy)
1.  [function <span class="apidocSignatureSpan">eventproxy.</span>create ()](#apidoc.element.eventproxy.create)



# <a name="apidoc.module.eventproxy"></a>[module eventproxy](#apidoc.module.eventproxy)

#### <a name="apidoc.element.eventproxy.EventProxy"></a>[function <span class="apidocSignatureSpan">eventproxy.</span>EventProxy ()](#apidoc.element.eventproxy.EventProxy)
- description and source-code
```javascript
EventProxy = function () {
  if (!(this instanceof EventProxy)) {
    return new EventProxy();
  }
  this._callbacks = {};
  this._fired = {};
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.eventproxy.create"></a>[function <span class="apidocSignatureSpan">eventproxy.</span>create ()](#apidoc.element.eventproxy.create)
- description and source-code
```javascript
create = function () {
  var ep = new EventProxy();
  var args = CONCAT.apply([], arguments);
  if (args.length) {
    var errorHandler = args[args.length - 1];
    var callback = args[args.length - 2];
    if (typeof errorHandler === 'function' && typeof callback === 'function') {
      args.pop();
      ep.fail(errorHandler);
    }
    ep.assign.apply(ep, args);
  }
  return ep;
}
```
- example usage
```shell
...
4. 友好的Error handling
5. 无平台依赖，适合前后端，能用于浏览器和Node.js
6. 兼容CMD，AMD以及CommonJS模块环境

现在的，无深度嵌套的，并行的

'''js
var ep = EventProxy.create("template", "data", "l10n", function (template, data, l10n) {
  _.template(template, data, l10n);
});

$.get("template", function (template) {
  // something
  ep.emit("template", template);
});
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
