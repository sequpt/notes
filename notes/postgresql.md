# postgresql

Open-source relational database management system(RDBMS).

- Website: <https://www.postgresql.org>
- Doc:     <https://www.postgresql.org/docs/current/index.html>
- Source:  <https://www.postgresql.org/ftp/source/>

## Installation

```text
# Create the file repository configuration:
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# Import the repository signing key:
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# Update the package lists:
sudo apt-get update

# Install the latest version of PostgreSQL.
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql'
sudo apt-get -y install postgresql
```

## Usage

### Short form

 ```text
 pg_dumpall -U admin -c --if-exists > <file>-`date -uIs`.sql #1 Make backup to a `sql` file postfixed with a timestamp in ISO 8601 format
 ```

### Long form

 ```text
 pg_dumpall --clean --if-exists -U admin > <file>-`date -uIs`.sql #1
 ```
