# c_escape
A small unicode (UTF-8 + surrogate pairs) escaper and unescaper for `C`. Both `C` and `JSON` flavored escaping are available.
```c
const char* str = "français\n日本 한국어";
printf("%s\n", str);
// français 
// 日本 한국어

// Escape the unicode!
char* escaped = escape(str, CE_JSON);
printf("%s\n", escaped);
// fran\u00E7ais\n\u65E5\u672C \uD55C\uAD6D\uC5B4

// Unescape the unicode!
char* unescaped = unescape(escaped, CE_JSON, NULL);
printf("%s\n", unescaped);
// français 
// 日本 한국어

free(escaped);
free(unescaped);

```

> **Warning**
>
> Invalid UTF-8/UTF-16 may cause `escape` to not work properly, and `unescape` to return `NULL`.

## Flavor comparison

|          | `CE_C` | `CE_JSON` |
|----------|--------|-----------|
| `\a`     | ✔️      | ❌         |
| `\b`     | ✔️      | ✔️         |
| `\e`     | ✔️      | ❌         |
| `\f`     | ✔️      | ✔️         |
| `\n`     | ✔️      | ✔️         |
| `\r`     | ✔️      | ✔️         |
| `\t`     | ✔️      | ✔️         |
| `\u0000` | ✔️      | ✔️         |
| `\v`     | ✔️      | ❌         |
| `\x00`   | ✔️      | ❌         |
| `\'`     | ✔️      | ✔️         |
| `\"`     | ✔️      | ✔️         |
| `\\`     | ✔️      | ✔️         |

## Usage

Just plop the `c_escape.h` and `c_escape.c` file into your project and `#include` it!
Make sure that `c_escape.c` is compiled.

## Contributing

Of course! Just make a pull request.

## Issues

If you find any bugs, just create an issue. I will fix it as soon as I can.
