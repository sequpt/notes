# npm

Node package manager.

- Homepage: <https://www.npmjs.com>
- Doc: <https://docs.npmjs.com>
- Repo: <https://github.com/npm/cli>

## Installation

`npm` is installed as part of [node](node.md)

## Update

```text
npm install npm@latest -g
```

## Usage

```text
npm init                          # Create new package(`package.json`)
npm install                       # Install all modules listed in `package.json`
npm install <package>             # Install <package> as a production dependency in local 'node_modules' folder
npm install <package> --save-prod # Same as above
npm install <package> --save-dev  # Install <package> as a development dependency in local 'node_modules' folder
npm install <package> --global    # Install <package> globally
npm update <package>              # Update local <package>
npm update <package> --global     # Update global <package>
npm uninstall <package>           # Uninstall local <package> and remove its reference from `package.json`
npm uninstall <package> --save    # Same as above
npm uninstall <package> --no-save # Uninstall local <package> but keep its reference in `package.json`
npm uninstall <package> --global  # Uninstall global <package>
npm ci                            # Clean install for automated environment(require `package-lock.json`)
npm version <major|minor|patch>   # Update the project version in the package* files (run `npm config set git-tag-version false` once before)
```
