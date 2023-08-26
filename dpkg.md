# dpkg

Debian package manager

- Website:  <https://www.dpkg.org>
- Doc:      <https://man7.org/linux/man-pages/man1/dpkg.1.html>
- Source:   <https://git.dpkg.org/git/dpkg/dpkg.git>
  - Mirror: <https://salsa.debian.org/dpkg-team/dpkg>

## Installation

- Debian: `sudo apt-get install dpkg`
  - Package is `essenial` and `required`

## Usage

### Short form

```text
dpkg -s             #1 Print status of all package(i.e., print `/var/lib/dpkg/status`)
dpkg -s <package>   #2 Print <package> status
dpkg -l             #3 Print list of installed packages(from `/var/lib/dpkg/status`)
dpkg -l "<pattern>" #4 Print list of packages matching <pattern>
dpkg -S "<pattern>" #5 Print list of packages which own files matching <pattern>
```

### Long form

```text
dpkg --status             #1
dpkg --status <package>   #2
dpkg --list               #3
dpkg --list "<pattern>"   #4
dpkg --search "<pattern>" #5
```
