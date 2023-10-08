# scp

OpenSSH secure file copy

- Website: <https://www.openssh.com/>
- Doc: <https://www.openssh.com/manual.html>
- Repo: <https://github.com/openssh/openssh-portable>

## Installation

- Debian: `sudo apt-get install openssh-client`

## Usage

```text
scp -r <user>@<hostname>:<remote-path> <local-path> # Recursively copy directory from remote server to local machine
```
