# curl

Send and receive things from the net.

- Website: <https://curl.se/>
- Repo: <https://github.com/curl/curl>

## Installation

- Debian: `sudo apt-get install curl`

## Usage

Alternative options names are shown between square brackets `[]`.

/!\ `curl` doesn't recognize options passed with an equal sign `=`:

- Valid  : `--<option> <value>`
- Invalid: `--<option>=<value>`

```text
curl <url>                                  # Download data from <url> and output it to `stdout`
curl --url <url>                            # Same as above
curl -i <url>                               # Include the HTTP response headers in the output [--include]
curl -O <url>                               # Download data to a file named from last part of <url> to the current directory [--remote-name]
curl -o <path> <url>                        # Download data to <path>(directories must exist) [--output]
curl -o <path> <url> --create-dirs          # Same as above but create directories if needed
curl -I <url>                               # Download the http header only [--head]
curl -s <url>                               # Silent mode [--silent]
curl -L <url>                               # Handle redirection [--location]
curl -o <path> -s -w "%{http_code}\n" <url> # Download data to <path> and print the status code to `stdout` [--write-out]
```
