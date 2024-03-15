# Minimum minimorum configure (Minmiconf) script

## Minmiconf is written for my humble needs to set values in a Makefile

### Notes

* **The project is on the very early stage of progress, nothing works!**
* `Minmiconf` is not an autotools configure script, you most probably do not need it

### Implemented functions

| Function          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
|`dprintf()`        |If debug mode is on print a message specified in `$*`                                             |
|`detect_path()`    |Print one or all (based on `$3`) pathname(s) from a list `$1` with permissions `$2`               |
|`detect_lib_path()`|Similar to above, detects valid library path(s) from a list                                       |
|`detect_library()` |Detect library with name `$1` exists using `$2` path(s) list as hints                             |
|`ifdebug()`        |If `DEBUG` value is `[yY1-9]` return `0`; `[nN0]`: `1`; on error: `2`                             |
|`write_vars()`     |Write/update variables specified in `$1` list and their values to a `$2` file                     |

### TO-DO List

| Function          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
|`detect_cc()`      |Try to detect C-language compiler                                                                 |

### Contacts

If you have an idea, a question, or have found a problem, do not hesitate to open an
[issue](https://github.com/mezantrop/ts-warp/issues/new/choose) or mail me: Mikhail Zakharov <zmey20000@yahoo.com>
