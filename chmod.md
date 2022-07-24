# chmod

Change file permission

## Installation

- Debian: `sudo apt-get install coreutils`

## Usage

### With letters

```console
# Give read right to user
chmod u+r <path>
# Give write right to user
chmod u+w <path>
# Give execution right to user
chmod u+x <path>
# Give read/write/executions rights to user
chmod u+rwx <path>
# Give execution right to group
chmod g+x <path>
# Give execution right to others
chmod o+x <path>
# Give execution right to all
chmod a+x <path>
# Give same rights as user to others
chmod o=u <path>
# Remove execution right from user
chmod u-x <path>
```

### With numbers

```console
# -rw-------
chmod 600 <path>
# -rw-r--r--
chmod 644 <path>
# -rwx------
chmod 700 <path>
# -rwxr-xr-x
chmod 755 <path>
# -rwxrwxrwx
chmod 777 <path>
```

## Permission reading

```text
drwxrwxrwx
|\_/\_/\_/
| |  |  |
| |  |  +---others rights
| |  +---group rights
| +---user rights
+---directory bit
```
