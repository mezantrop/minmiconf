# Minimum minimorum configure (Minmiconf)

## Minmiconf script is written for my humble needs to set values in a Makefile

### Notes

* **The project is on the very early stage of progress, nothing works!**
* `Minmiconf` is not an autotools configure script, you most probably do not need it

### TO-DO List

| Status | Function                 | Description                                                                      |
|--------|--------------------------|----------------------------------------------------------------------------------|
| [x]    | `dprintf("$*")`          | If debug mode is on print a message specified in `$*`                            |
| [x]    | `detect_path("$1" "$2")` | Detect a valid pathname in a list: `$1` accounting file-permissions: `$2`        |
| [x]    | `ifdebug()`              | If `DEBUG` value is `[yY1-9]` return `0`; `[nN0]` return `1`; On error return `2`|
| [x]    | `write_vars("$1" "$2")`  | Write/update variables specified in `$1` list and their values to/in a `$2` file |

### Contacts

If you have an idea, a question, or have found a problem, do not hesitate to open an
[issue](https://github.com/mezantrop/ts-warp/issues/new/choose) or mail me: Mikhail Zakharov <zmey20000@yahoo.com>
