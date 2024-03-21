# Minimum minimorum configure (Minmiconf) script

## Minmiconf is written for my humble needs to set values in a Makefile

### Notes

* **The project is on the very early stage of development, nothing works, don't even try!**
* This not an [autotools](https://www.gnu.org/software/automake/manual/html_node/Autotools-Introduction.html) `configure` script
* There are many better alternatives: less complex or having more functionality, but I like inventing bicycles
* Yes, you most probably, do not need `Minmiconf`

### Description

#### mconfigure anathomy

* Script maintenance variables, with names staring with "_" character
* Global default variables
* Function definitions:
  * Script maintaining functions, with names staring with "_" character, e.g., `_dprintf()`
  * `detect_*()` functions: return existence/status of something
  * `define_*()` functions: set/change variable in memory, e.g., `WITH_*` variables
  * `decide_*()` functions: decide yes/no if argument is acceptable
  * `write_*()` functions: Modify `Makefile` or other files
  * User-difined functions
* Processing body

### Implemented functions

#### Script maintaining functions

| Function          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
|`_dprintf()`       |If debug mode is on print a message specified in `$*`                                             |
|`_ifdebug()`       |If `_DEBUG` value is `[yY1-9]` return `0`; `[nN0]`: `1`; on error: `2`                            |
|`_in()`            |String-in-string. Return `0` if `$2` is in `$1`, otherwise return `1`                             |

#### Detect functions

| Function          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
|`detect_cc()`      |Detect C-compiler; `$1`: Results variable; `$2`: Compiler candidates in addition to CC_CANDIDATES |
|`detect_path()`    |Print one or all (based on `$4`) pathname(s) from a list `$2` with permissions `$3`; Result in`$1`|
|`detect_lib_path()`|Similar to above, detects valid library path(s) from a list                                       |
|`detect_library()` |Detect library with name `$2` exists using `$3` path(s) list as hints; Result in`$1`              |
|`detect_target()`  |Detect target triplet: machine-vendor-os; Result in`$1`                                           |
|`detect_user()`    |Detect current username; Respects `USER` and `WITH_USER` variables; `$1`: Results variable        |

#### Output functions

| Function     | Description                                                                                           |
|--------------|-------------------------------------------------------------------------------------------------------|
|`check    ()` |Check and print `yes/no`; `$1`: `f()` to run; `$2`: result arg of `f()`; `$3` the rest args of `f()`   |
|`write_vars()`|Write/update variables specified in `$1` list and their values to a `$2` file                          |

### TO-DO List

| Function          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
|                   |                                                                 |

### Contacts

If you have an idea, a question, or have found a problem, do not hesitate to open an
[issue](https://github.com/mezantrop/ts-warp/issues/new/choose) or mail me: Mikhail Zakharov <zmey20000@yahoo.com>
