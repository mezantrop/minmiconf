# Minimum minimorum configure (Minmiconf) script

## Minmiconf is written for my humble needs to set values in Makefiles

### Notes

* **The project is on the early stage of development, don't be surprised to face issues!**
* This not an [autotools](https://www.gnu.org/software/automake/manual/html_node/Autotools-Introduction.html) `configure` script
* There are many better alternatives: less complex or having more functionality, but I like inventing bicycles
* Yes, you most probably, do not need `Minmiconf`

### Description

#### (m)configure anathomy

* Script maintenance variables, with names staring with "_" character
* Global default variables
* Function definitions:
  * Script maintaining functions, with names staring with "_" character, e.g., `_dprintf()`
  * Process control, conditionsl, etc functions
  * `DETECT_*()` functions: return existence/status of something
  * `DEFINE_*()` functions: set/change variable in memory, e.g., `WITH_*` variables
  * `DECIDE_*()` functions: decide yes/no if argument is acceptable
  * `WRITE_*()` functions: Modify `Makefile` or other files
  * User-difined functions
* Processing body

### Implemented functions

#### Maintenance functions

| Function        | Description                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------|
|`_DPRINTF`       |If debug mode is on print a message specified in `$*`                                               |
|`_IFDEBUG`       |If `_DEBUG` value is `[yY1-9]` return `0`; `[nN0]`: `1`; on error: `2`. See `_YN()`                 |
|`_SELF_CHK`      |Quick mandatory selfcheck                                                                           |
|`_YN`            |If `$1` value is `[yY1-9]` return `0`; `[nN0]`: `1`; on error: `2`                                  |

#### Process control functions

| Function        | Description                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------|
|`EHARD`/`ESOFT`  |Define functions behavior on an error: `EHARD`: `exit 1`, `ESOFT`: `return 1`                       |
|`IF_NDEF_OR_IVAR`|IF `$1` variable is NOT defined or has `$2` numeric value, return `0` otherwise return `1`          |
|`IN`             |String-in-string. Return `0` if `$2` is in `$1` string, otherwise return `1`                        |
|`IN_VAR`         |String-in-variable. Return `0` if `$2` is in `$1` variable, otherwise return `1`                    |

#### Detect functions

| Function        | Description                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------|
|`DETECT_CC`      |Detect C-compiler; `$1`: Results variable; `$2`: Compiler candidates in addition to `CC_CANDIDATES` |
|`DETECT_COMMAND` |Detect `$2` command existence; Results variable: `$1`; Return: `0` - on success, `1` if not         |
|`DETECT_PATH`    |Print one or all (based on `$4`) pathname(s) from a list `$2` with permissions `$3`; Result in`$1`  |
|`DETECT_PREFIX`  |Forcibly sets prefix from `PREFIX` variable, or detects if from `$2` or `PREFIX_PATH_CANDIDATES`    |
|`DETECT_IPATH`   |Similar to `DETECT_PATH()`, detects valid include path(s) from a list                               |
|`DETECT_LPATH`   |Similar to `DETECT_PATH()`, detects valid library path(s) from a list                               |
|`DETECT_LIBRARY` |Detect library with name `$2` exists using `$3` path(s) list as hints; Result in`$1`                |
|`DETECT_TARGET`  |Detect target triplet: machine-vendor-os; Result in`$1`                                             |
|`DETECT_USER`    |Detect current username; Respects `USER` and `WITH_USER` variables; `$1`: Results variable          |

#### Define and Output functions

| Function        | Description                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------|
|`CONFIG_CLEAN`   |Remove configuration lock; `$1`: Results variable; `$2`: lock-file, default: `.configured`          |
|`CONFIG_FINISH`  |Finish configuration; `$1`: Results var, `$2`: lock, default `.configured`; Returns `0`: OK, `1`: KO|
|`CONFIG_START`   |Start config; `$1`: Results var, `$2`: lock, default `.configured`; `$3` = `[fF]` force!; Returns `0`: OK, `1`: KO|
|`DECIDE`         |Check and print `yes/no`; `$1`: `f()` to run; `$2`: result arg of `f()`; `$3` the rest args of `f()`|
|`DEFINE_VAR`     |Define a variable and set its value; `$1`: Results variable; `$2`: the value; Always returns `0`    |
|`NOTIFY`         |Print `$2`: message with a premble `$1`; Always returns `0`                                         |
|`WRITE_VARS`     |Write/update variables specified in `$1` list and their values to a `$2` file                       |

### TO-DO List

| Function        | Description                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------|
|                 |                                                                                                    |

### Contacts

If you have an idea, a question, or have found a problem, do not hesitate to open an
[issue](https://github.com/mezantrop/ts-warp/issues/new/choose) or mail me: Mikhail Zakharov <zmey20000@yahoo.com>
