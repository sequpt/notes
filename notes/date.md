# date

Print or set the system date and time

## Installation

- Debian: `sudo apt-get install coreutils`

## Usage

A `[GNU]` in the comment indicates that the command is only possible with the
GNU variant of the program.

### Short form

```console
date -uIs             #1 Print current date in ISO 8601 format with seconds precision and time zone set to UTC
date -uIs -d "<date>" #2 Convert <date> to the same format as in #1(<date> example: "Thu, 12 Jan 2023 08:16:44") [GNU]
```

### Long form

```console
date --iso-8601=seconds --utc                 #1
date --iso-8601=seconds --utc --date "<date>" #2 [GNU]
```
