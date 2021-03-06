
<!--introduced_in=v7.10.0-->
<!-- type=misc -->

> Stability: 2 - Stable

N-API (pronounced N as in the letter, followed by API)
is an API for building native Addons. It is independent from
the underlying JavaScript runtime (ex V8) and is maintained as part of
Node.js itself. This API will be Application Binary Interface (ABI) stable
across versions of Node.js. It is intended to insulate Addons from
changes in the underlying JavaScript engine and allow modules
compiled for one major version to run on later major versions of Node.js without
recompilation. The [ABI Stability][] guide provides a more in-depth explanation.

Addons are built/packaged with the same approach/tools
outlined in the section titled [C++ Addons](addons.html).
The only difference is the set of APIs that are used by the native code.
Instead of using the V8 or [Native Abstractions for Node.js][] APIs,
the functions available in the N-API are used.

APIs exposed by N-API are generally used to create and manipulate
JavaScript values. Concepts and operations generally map to ideas specified
in the ECMA262 Language Specification. The APIs have the following
properties:
- All N-API calls return a status code of type `napi_status`. This
  status indicates whether the API call succeeded or failed.
- The API's return value is passed via an out parameter.
- All JavaScript values are abstracted behind an opaque type named
  `napi_value`.
- In case of an error status code, additional information can be obtained
  using `napi_get_last_error_info`. More information can be found in the error
  handling section [Error Handling][].

The N-API is a C API that ensures ABI stability across Node.js versions
and different compiler levels. However, we also understand that a C++
API can be easier to use in many cases. To support these cases we expect
there to be one or more C++ wrapper modules that provide an inlineable C++
API. Binaries built with these wrapper modules will depend on the symbols
for the N-API C based functions exported by Node.js. These wrappers are not
part of N-API, nor will they be maintained as part of Node.js. One such
example is: [node-addon-api](https://github.com/nodejs/node-addon-api).

