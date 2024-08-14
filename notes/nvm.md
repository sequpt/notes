# nvm

Node version manager.

- Homepage: <https://github.com/nvm-sh/nvm>
- Doc: <https://github.com/nvm-sh/nvm>
- Repo: <https://github.com/nvm-sh/nvm>

## Installation

```text
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/HEAD/install.sh | bash
source ~/.bashrc
```

## Update

```text
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/HEAD/install.sh | bash
```

## Usage

`<node-version>` can be one of the following:

- `node`: the latest version of node
- `--lts`: the long-term support version
- `<x.y.z>`: a version number like `19.8.1`

```text
nvm install <node-version>       # Install node
nvm use <node-version>           # Select <node-version> for the current shell
nvm alias default <node-version> # Set <node-version> as the default
nvm ls                           # List installed node versions
nvm ls-remote                    # List available node versions
nvm run node --version           # Run 'node --version'
nvm exec node --version          # Run 'node --version' in a subshell
```
