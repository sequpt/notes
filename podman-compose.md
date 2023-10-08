# podman-compose

docker-compose alternative

- Website: <https://github.com/containers/podman-compose>
- Code: <https://github.com/containers/podman-compose>

## Prerequisites

- dnsmasq: `sudo apt-get install dnsmasq`
- dsname:

  ```text
  git clone https://github.com/containers/dnsname.git/
  cd dnsname
  make all PREFIX="$HOME/.local"
  make install PREFIX="$HOME/.local"
  ```

## Installation

```text
python3 -m pip install podman-compose
```

## Configuration

- `containers.conf`: <https://github.com/containers/common/blob/main/docs/containers.conf.5.md>

```text
cat >> "$HOME/.config/containers/containers.conf" << EOF

[network]
cni_plugin_dirs = [
    "$HOME/.local/libexec/cni",
    "/usr/lib/cni"
]
EOF
```

## Usage

```text
podman-compose build
podman-compose up
podman-compose down
podman-compose --file <path> build
```
