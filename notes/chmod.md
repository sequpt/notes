# chmod

Change file permission.

## Installation

- Debian package: `coreutils`

## Permission reading

```text
r: read
w: write
x: execute

drwxrwxrwx
|\_/\_/\_/
| |  |  |
| |  |  +---others rights
| |  +---group rights
| +---user rights
+---directory bit
```

## Usage

### With letters

```console
chmod u+r <path>   # Give read right to user
chmod u+w <path>   # Give write right to user
chmod u+x <path>   # Give execution right to user
chmod u+rwx <path> # Give read/write/executions rights to user
chmod g+x <path>   # Give execution right to group
chmod o+x <path>   # Give execution right to others
chmod a+x <path>   # Give execution right to all
chmod o=u <path>   # Give same rights as user to others
chmod u-x <path>   # Remove execution right from user
```

### With numbers

```console
chmod 600 <path> # -rw-------
chmod 644 <path> # -rw-r--r--
chmod 700 <path> # -rwx------
chmod 755 <path> # -rwxr-xr-x
chmod 777 <path> # -rwxrwxrwx
```
