# cloc

Count lines of code.

- Repo: <https://github.com/AlDanial/cloc>

## Installation

- Debian: `sudo apt-get install cloc`

## Usage

```console
# Process files recursively starting from <path> and exclude all files and
# directories in <file>
cloc --exclude-list-file=<file> <path>
# Example
cloc --exclude-list-file=.clocignore .
```

`.clocignore` contains paths like this:

```text
.clang-format
.clang-tidy
Makefile
build
compile_commands.json
doc
examples
```
