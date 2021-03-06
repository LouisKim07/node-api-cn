<!-- YAML
added: v0.1.31
changes:
  - version: v7.6.0
    pr-url: https://github.com/nodejs/node/pull/10739
    description: The `target` and `path` parameters can be WHATWG `URL` objects
                 using `file:` protocol. Support is currently still
                 *experimental*.
-->

* `target` {string|Buffer|URL}
* `path` {string|Buffer|URL}
* `type` {string} 默认为 `'file'`。
* `callback` {Function}
  * `err` {Error}

异步的 symlink(2)。
完成回调只有一个可能的异常参数。
`type` 参数可以设为 `'dir'`、`'file'` 或 `'junction'`，且仅在 Windows 上有效（在其他平台上忽略）。
Windows 上使用 `'junction'` 要求目标路径是绝对路径。
当使用 `'junction'` 时，`target` 参数会被自动标准化为绝对路径。

例子，创建了一个名为 "new-port" 且指向 "foo" 的符号链接：

```js
fs.symlink('./foo', './new-port', callback);
```

