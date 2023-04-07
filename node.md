# node

JavaScript runtime

- Website: <https://nodejs.org/>
- Source : <https://github.com/nodejs/node>
- nvm: <https://github.com/nvm-sh/nvm>
- npm: [website](https://www.npmjs.com/)/[repo](https://github.com/npm/cli)

## Installation

### nvm

```text
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
source ~/.bashrc
```

### node LTS

```text
nvm install --lts
```

## Usage

```text
nvm ls                            # list node versions
npm init                          # Create new package or initialize an existing one
npm install <package>             # Install <package> as a production dependency in local 'node_modules' folder
npm install <package> --save-prod # Same as above
npm install <package> --save-dev  # Install <package> as a development dependency in local 'node_modules' folder
```
