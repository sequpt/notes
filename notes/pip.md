# pip

Package installer for Python.

- Homepage: <https://pip.pypa.io>
- Repo: <https://github.com/pypa/pip>

## Installation

- Debian package: `python3 python3-pip`

## Update

`python3 -m pip install --upgrade pip`

## Usage

```text
python3 -m pip --version                    # Print pip version
python3 -m pip install <package>            # Install package
python3 -m pip install <package>==<version> # Install a specific version of the package
python3 -m pip install --upgrade <package>  # Update package
python3 -m pip uninstall <package>          # Remove package
python3 -m pip list                         # List installed packages
```
