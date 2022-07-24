# curl

Send and receive things from the net.

- Website: <https://curl.se/>
- Repo: <https://github.com/curl/curl>

## Installation

- Debian: `sudo apt-get install curl`

## Usage

```text
curl -O <url>            : Download <url> to current directory (--remote-name)
curl <url> -o <path>     : Download <url> to <path> (--output)
curl -I <url>            : Download the http header only (--head)
curl -s <cmd>            : Silent mode (--silent)
curl -L <cmd>            : Handle redirection (--location)
curl --create-dirs <cmd> : Create the directories as needed
```
