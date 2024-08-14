# chown

Change file owner and group

## Installation

- Debian: `sudo apt-get install coreutils`

## Usage

### Short form

```console
chown <owner>:<group> <file>         #1 Set <file> owner and group to <owner>:<group>
chown <owner>:<group> *              #2 Set <owner>:<group> as owner and group for everything in the current directory
chown -R <owner>:<group> <directory> #3 Set <directory> owner and group to <owner>:<group> recursively
chown -R <owner>:<group> *           #4 Set Set <owner>:<group> as owner and group for everything in the current directory recursively
```

### Long form

```text
chown <owner>:<group> <file>                  #1
chown <owner>:<group> *                       #2
chown --recursive <owner>:<group> <directory> #3
chown --recursive <owner>:<group> *           #4
```
