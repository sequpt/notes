# podman

A tool for managing OCI containers and pods.

- Website      : <https://podman.io/>
- Documentation: <https://docs.podman.io/en/latest/>
- Source       : <https://github.com/containers/podman>

## Installation

<https://podman.io/getting-started/installation>

- Debian: `sudo apt-get install podman`

Debian version is old, it's better to install from sources.

## Build from sources

### Prerequisites

- Golang: <https://go.dev>

```text
# Download latest stable version to current directory
curl \
    --create-dirs \
    --location \
    --output "go.tar.gz" \
    --silent \
    --url "https://go.dev/dl/go$(\
        curl \
            --silent \
            --url "https://go.dev/dl/?mode=json" \
        | sed \
            --expression="3s/^\s*\"version\": \"go\(.*\)\",$/\1/p" \
            --silent \
        ).linux-amd64.tar.gz"
# Extract compressed archive to install directory
tar \
    --directory="$HOME/.local/app/" \
    --extract \
    --file="go.tar.gz"
# Delete compressed archive
rm "go.tar.gz"
# Add soft links to `go` and `gofmt` in `$HOME/.local/bin/`
ln -s "$HOME/.local/app/go/bin/go" "$HOME/.local/bin/go"
ln -s "$HOME/.local/app/go/bin/gofmt" "$HOME/.local/bin/gofmt"
```

### Build dependencies

```sh
sudo apt-get install \
    libapparmor-dev \
    libbtrfs-dev \
    libdevmapper-dev \
    libgpgme-dev \
    libseccomp-dev \
    libsystemd-dev
```

### Runtime dependencies

```text
sudo apt-get install \
    conmon \
    containernetworking-plugins \
    crun \
    fuse-overlayfs \
    slirp4netns \
    uidmap
```

The static builds of `conmon` available in the [github
repository](https://github.com/containers/conmon/releases) don't statically link
to `systemd` (see [this
comment](https://github.com/containers/conmon/issues/348#issuecomment-1222081803)).\
Running a container will fail with the following error message: `Error: write
child: broken pipe` because the default logging driver is `journald`.\
The possible solutions are:

- Installing the official `conmon` package from the `Debian` repository.
- Building `conmon` manually with `libsystemd-dev` installed.
- Add `log_driver = "<not-journald>"`(with `<not-journald>` being either
  `k8s-file`, `none` or `passthrough`) under the `[containers]` table in the
  `containers.conf` file.
- Run the `podman run` command with
  `--log-driver="<not-journald>"`.

### Build podman

- Branch `master` is unstable.
- Stable versions have tags with the following format: `v[0-9].[0-9].[0-9](.[0-9])?`.
  - Examples: `v4.0`, `v4.3.1`.

```text
git clone https://github.com/containers/podman.git
cd podman
# Checkout latest stable version
git checkout "$(\
    curl \
        --silent \
        --url "https://api.github.com/repos/containers/podman/releases/latest" \
    | sed \
        --expression="s/^\s*\"tag_name\": \"\(.*\)\",$/\1/p" \
        --silent \
    )"
make BUILDTAGS="apparmor seccomp systemd"
make install PREFIX="$HOME/.local"
```

## Configure

- `containers.conf`: <https://github.com/containers/common/blob/main/docs/containers.conf.5.md>

```text
cat > "$HOME/.config/containers/containers.conf" << EOF
# The container engine configuration file specifies default configuration
# options and command-line flags for container engines.

[engine]
helper_binaries_dir = [
    "$HOME/.local/libexec/podman"
]
EOF
```

- `policy.json`: <https://github.com/containers/image/blob/main/docs/containers-policy.json.5.md>

```text
# This configuration allows all images without any requirements.
cat > "$HOME/.config/containers/policy.json" << EOF
{
    "default": [
        {
            "type": "insecureAcceptAnything"
        }
    ]
}
EOF
```

- `registries.conf`: <https://github.com/containers/image/blob/main/docs/containers-registries.conf.5.md>

```text
cat > "$HOME/.config/containers/registries.conf" << EOF
# System-wide configuration file for container image registries.

# An array of `host[:port]` registries to try when pulling an unqualified image,
# in order.
unqualified-search-registries = ["docker.io"]

# - If only one unqualified-search registry is set, use it as there is no
#   ambiguity.
# - If there is more than one registry and the user program is running in a
#   terminal (i.e., stdout & stdin are a TTY), prompt the user to select one of
#   the specified search registries.
# - If the program is not running in a terminal, the ambiguity cannot be
#   resolved which will lead to an error.
short-name-mode = "enforcing"
EOF
```

- `storage.conf`: <https://github.com/containers/storage/blob/main/docs/containers-storage.conf.5.md>

```text
cat > "$HOME/.config/containers/storage.conf" << EOF
[storage]
driver = "overlay"
[storage.options.overlay]
mount_program = "/usr/bin/fuse-overlayfs"
EOF
```

- `podman.socket`

```text
# Create symlink $HOME/.config/systemd/user/sockets.target.wants/podman.socket → $HOME/.local/lib/systemd/user/podman.socket.
# Create symlink $HOME/.config/systemd/user/podman.socket → $HOME/.local/lib/systemd/user/podman.socket.
systemctl --user enable $HOME/.local/lib/systemd/user/podman.service

# Create symlink $HOME/.config/systemd/user/default.target.wants/podman.service → $HOME/.local/lib/systemd/user/podman.service.
# Create symlink $HOME/.config/systemd/user/podman.service → $HOME/.local/lib/systemd/user/podman.service.
systemctl --user enable $HOME/.local/lib/systemd/user/podman.socket

# Start podman.socket
systemctl --user start podman.socket

# Verify that podman.socket is started
systemctl --user status podman.socket
```
