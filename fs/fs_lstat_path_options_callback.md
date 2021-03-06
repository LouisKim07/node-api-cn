<!-- YAML
added: v0.1.30
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/12562
    description: The `callback` parameter is no longer optional. Not passing
                 it will throw a `TypeError` at runtime.
  - version: v7.6.0
    pr-url: https://github.com/nodejs/node/pull/10739
    description: The `path` parameter can be a WHATWG `URL` object using `file:`
                 protocol. Support is currently still *experimental*.
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/7897
    description: The `callback` parameter is no longer optional. Not passing
                 it will emit a deprecation warning with id DEP0013.
  - version: v10.5.0
    pr-url: https://github.com/nodejs/node/pull/20220
    description: Accepts an additional `options` object to specify whether
                 the numeric values returned should be bigint.
-->

* `path` {string|Buffer|URL}
* `options` {Object}
  * `bigint` {boolean} [`fs.Stats`] 对象返回的数值是否为长整数型。默认为 `false`。
* `callback` {Function}
  * `err` {Error}
  * `stats` {fs.Stats}

异步的 lstat(2)。
回调有两个参数 `(err, stats)`，其中 `stats` 是一个 [`fs.Stats`] 对象。
`lstat()` 与 [`stat()`] 的区别是，如果 `path` 是一个符号链接，则链接指向自身而不是文件。

