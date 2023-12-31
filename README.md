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
- [`body([fields, message])`](https://express-validator.github.io/docs/api/check/#body)

  ```js
  [
    // …
    body("name", "Empty name").trim().isLength({ min: 1 }).escape(),
    // …
  ];
  ```
  - defines that we're checking the "name" field.
  - a validation error will set an error message "Empty name".
  - We then call the sanitization method `trim()` to remove whitespace from the start and end of the string.
  - `isLength()` to check the resulting string isn't empty.
  - Finally, we call `escape()` to remove HTML characters from the variable that might be used in JavaScript cross-site scripting attacks.

  This test checks that the age field is a valid date and uses optional() to specify that null and empty strings will not fail validation.

  ```js
  [
    // …
    body("age", "Invalid age")
      .optional({ values: "falsy" })
      .isISO8601()
      .toDate(),
    // …
  ];
  ```
  You can also daisy chain different validators, and add messages that are displayed if the preceding validators are false.
  ```js
  [
    // …
    body("name")
      .trim()
      .isLength({ min: 1 })
      .withMessage("Name empty.")
      .isAlpha()
      .withMessage("Name must be alphabet letters."),
    // …
  ];
  ```
- [`validationResult(req)`](https://express-validator.github.io/docs/api/validation-result/#validationresult)

  Runs the validation, making errors available in the form of a validation result object. This is invoked in a separate callback, as shown below:

  ```js  
  asyncHandler(async (req, res, next) => {
    // Extract the validation errors from a request.
    const errors = validationResult(req);
  
    if (!errors.isEmpty()) {
      // There are errors. Render form again with sanitized values/errors messages.
      // Error messages can be returned in an array using `errors.array()`.
    } else {
      // Data from form is valid.
    }
  });
  ```
  We use the validation result's isEmpty() method to check if there were errors, and its array() method to get the set of error messages.
