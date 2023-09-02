<div align="center">
  <h1><a href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Tutorial_local_library_website">Local Library Tutorial</a></h1>
  
  ![mvc_express](https://github.com/yousefelassal/LocalLibrary/assets/76617202/b14b051f-68cf-49ed-8d2c-c4599fea6f06)

</div>


## [Route paths](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes#route_paths)


- `?` : The endpoint must have 0 or 1 of the preceding character (or group), e.g. a route path of `'/ab?cd'` will match endpoints `acd` or `abcd`.
- `+` : The endpoint must have 1 or more of the preceding character (or group), e.g. a route path of `'/ab+cd'` will match endpoints `abcd`, `abbcd`, `abbbcd`, and so on.
- `*` : The endpoint may have an arbitrary string where the `*` character is placed. E.g. a route path of `'/ab*cd'` will match endpoints `abcd`, `abXcd`, `abSOMErandomTEXTcd`, and so on.
- `()` : Grouping match on a set of characters to perform another operation on, e.g. `'/ab(cd)?e'` will perform a `?`-match on the group `(cd)` — it will match `abe` and `abcde`.

## [Express Validator](https://express-validator.github.io/docs)
