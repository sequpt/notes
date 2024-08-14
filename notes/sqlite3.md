# sqlite3

SQL database engine.

- Homepage: <https://www.sqlite.org/>
- Doc: <https://www.sqlite.org/docs.html>
- Repo
  - <https://github.com/sqlite/sqlite>
  - <https://sqlite.org/src>

## Installation

- Debian package: `sqlite3`

## Usage

### Export table to json

```sh
sqlite3 \
        "<db_path>" \
        ".mode .json" \
        ".once <output_path>" \
        "SELECT * FROM <TABLE>;"
```

Or

```sh
sqlite3 -json "<db_path>" "SELECT * FROM <TABLE>;" > "<output_path>"
```
