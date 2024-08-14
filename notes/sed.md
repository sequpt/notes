# sed

Stream editor for filtering and transforming text

- Website: <https://www.gnu.org/software/sed/>
- Doc: <https://www.gnu.org/software/sed/manual/sed.html>
- Repo: <https://git.savannah.gnu.org/cgit/sed.git>

## Installation

- Debian: `sudo apt-get install sed`

## Usage

```text
sed -e 's/<regex>/<replcm>/'   : Replace <regex> with <replcm>
sed -e 's|<regex>|<replcm>|'   : To use if there is a `/` in the text to replace
sed -ne 's/<regex>/<replcm>/p' : Don't print text if <regex> doesn't match
sed -e 's/\(<regex>\)/\1/'     : Replace <regex> with captured group `\1`
`+` must be escaped => [0-9]\+
```
