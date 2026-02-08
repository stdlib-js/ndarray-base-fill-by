<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# fillBy

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Fill an input ndarray according to a callback function.

<section class="intro">

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import fillBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-fill-by@esm/index.mjs';
```

#### fillBy( x, fcn\[, thisArg] )

Fills an input ndarray according to a callback function.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

function fcn() {
    return 10.0;
}

var x = array( [ [ [ 1.0, 2.0 ] ], [ [ 3.0, 4.0 ] ], [ [ 5.0, 6.0 ] ] ] );
// returns <ndarray>[ [ [ 1.0, 2.0 ] ], [ [ 3.0, 4.0 ] ], [ [ 5.0, 6.0 ] ] ]

var out = fillBy( x, fcn );
// returns <ndarray>[ [ [ 10.0, 10.0 ] ], [ [ 10.0, 10.0 ] ], [ [ 10.0, 10.0 ] ] ]

var bool = ( out === x );
// returns true
```

The function accepts the following arguments:

-   **x**: array-like object containing an input ndarray.
-   **fcn**: callback function.
-   **thisArg**: callback function execution context (_optional_).

To set the callback function execution context, provide a `thisArg`.

<!-- eslint-disable no-invalid-this -->

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

function fcn( value ) {
    return value * 10.0;
}

var x = array( [ [ [ 1.0, 2.0 ] ], [ [ 3.0, 4.0 ] ], [ [ 5.0, 6.0 ] ] ] );
// returns <ndarray>[ [ [ 1.0, 2.0 ] ], [ [ 3.0, 4.0 ] ], [ [ 5.0, 6.0 ] ] ]

var ctx = {
    'factor': 10.0
};

var out = fillBy( x, fcn, ctx );
// returns <ndarray>[ [ [ 10.0, 20.0 ] ], [ [ 30.0, 40.0 ] ], [ [ 50.0, 60.0 ] ] ]

var bool = ( out === x );
// returns true
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   A provided ndarray should be an object with the following properties:

    -   **dtype**: data type.
    -   **data**: data buffer.
    -   **shape**: dimensions.
    -   **strides**: stride lengths.
    -   **offset**: index offset.
    -   **order**: specifies whether an ndarray is row-major (C-style) or column major (Fortran-style).

-   The callback function is provided the following arguments:

    -   **value**: current array element.
    -   **indices**: current array element indices.
    -   **arr**: the input ndarray.

-   The function **mutates** the input ndarray.

-   The function assumes that each element in the underlying input ndarray data buffer has one, and only one, corresponding element in input ndarray view (i.e., a provided ndarray is not a broadcasted ndarray view).

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

var discreteUniform = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-discrete-uniform' ).factory;
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import zeros from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-zeros@esm/index.mjs';
import fillBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-fill-by@esm/index.mjs';

// Create a zero-filled ndarray:
var x = zeros( [ 5, 2 ], {
    'dtype': 'generic'
});
console.log( ndarray2array( x ) );

// Fill the ndarray with random values:
fillBy( x, discreteUniform( -100, 100 ) );
console.log( ndarray2array( x ) );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-base-fill-by.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-base-fill-by

[test-image]: https://github.com/stdlib-js/ndarray-base-fill-by/actions/workflows/test.yml/badge.svg?branch=v0.1.1
[test-url]: https://github.com/stdlib-js/ndarray-base-fill-by/actions/workflows/test.yml?query=branch:v0.1.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-base-fill-by/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-base-fill-by?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-base-fill-by.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-base-fill-by/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-base-fill-by/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-base-fill-by/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-base-fill-by/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-base-fill-by/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-base-fill-by/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-base-fill-by/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-base-fill-by/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-base-fill-by/main/LICENSE

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
