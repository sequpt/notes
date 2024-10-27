# docker

Application container.

- Homepage: <https://www.docker.com/>
- Doc: <https://docs.docker.com/>
- Repo: <https://github.com/moby/moby>

## Table of Contents

- [docker](#docker)
  - [Table of Contents](#table-of-contents)
  - [Install](#install)
    - [Rootful](#rootful)
    - [Rootless](#rootless)
  - [Uninstall](#uninstall)
    - [Rootful](#rootful-1)
      - [Remove packages](#remove-packages)
      - [Remove images, containers and configuration files](#remove-images-containers-and-configuration-files)
      - [Remove source list and keyrings](#remove-source-list-and-keyrings)
    - [Rootless](#rootless-1)
      - [Remove daemon](#remove-daemon)
      - [Remove binaries](#remove-binaries)
      - [Remove images, containers and configuration files](#remove-images-containers-and-configuration-files-1)
  - [Usage](#usage)
  - [Scan image](#scan-image)

## Install

### Rootful

```text
# Add GPG key
sudo apt-get install \
  ca-certificates \
  curl
sudo install -m 0755 -d "/etc/apt/keyrings"
sudo curl -fsSL "https://download.docker.com/linux/debian/gpg" -o "/etc/apt/keyrings/docker.asc"
sudo chmod a+r "/etc/apt/keyrings/docker.asc"

# Add repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" \
  | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install packages
sudo apt-get update && sudo apt-get install \
  containerd.io \
  docker-buildx-plugin \
  docker-ce \
  docker-ce-cli \
  docker-compose-plugin
```

### Rootless

```text
# Install dependencies
sudo apt-get install \
  ca-certificates \
  curl \
  dbus-user-session \
  slirp4netns \
  uidmap

# Install docker
curl -fsSL "https://get.docker.com/rootless" | DOCKER_BIN="$HOME/.local/bin" sh

# Add to `~/.bashrc`
export DOCKER_HOST="unix://$XDG_RUNTIME_DIR/docker.sock"
export DOCKER_CONFIG="$XDG_CONFIG_HOME/docker"
# Source .bashrc
. "$HOME/.bashrc"

# Install docker compose plugin
mkdir -p "$DOCKER_CONFIG/cli-plugins"
curl -fsSL \
  "https://github.com/docker/compose/releases/download/v2.29.7/docker-compose-linux-x86_64" \
  -o "$DOCKER_CONFIG/cli-plugins/docker-compose"
chmod +x "$DOCKER_CONFIG/cli-plugins/docker-compose"

# Start daemon on system startup
sudo loginctl enable-linger $(whoami)
```

## Uninstall

### Rootful

#### Remove packages

```text
# docker.io, docker-compose, docker-doc and podman-docker are unofficial
# packages.
sudo apt-get remove --purge \
  containerd \
  containerd.io \
  docker-buildx-plugin \
  docker-ce \
  docker-ce-cli \
  docker-ce-rootless-extras \
  docker-compose \
  docker-compose-plugin \
  docker-doc \
  docker.io \
  podman-docker \
  runc
```

#### Remove images, containers and configuration files

```text
sudo rm -rf "/var/lib/docker"
sudo rm -rf "/var/lib/containerd"
```

#### Remove source list and keyrings

```text
sudo rm -f "/etc/apt/sources.list.d/docker.list"
sudo rm -f "/etc/apt/keyrings/docker.asc"
```

### Rootless

#### Remove daemon

```text
dockerd-rootless-setuptool.sh uninstall
```

#### Remove binaries

```text
rm -f \
  "$HOME.local/bin/containerd" \
  "$HOME.local/bin/containerd-shim" \
  "$HOME.local/bin/containerd-shim-runc-v2" \
  "$HOME.local/bin/ctr" \
  "$HOME.local/bin/docker" \
  "$HOME.local/bin/docker-init" \
  "$HOME.local/bin/docker-proxy" \
  "$HOME.local/bin/dockerd" \
  "$HOME.local/bin/dockerd-rootless-setuptool.sh" \
  "$HOME.local/bin/dockerd-rootless.sh" \
  "$HOME.local/bin/rootlesskit" \
  "$HOME.local/bin/rootlesskit-docker-proxy" \
  "$HOME.local/bin/runc" \
  "$HOME.local/bin/vpnkit"
```

#### Remove images, containers and configuration files

```text
sudo rm -rf "$DOCKER_CONFIG"
sudo rm -rf "$XDG_DATA_HOME/docker"
```

## Usage

```text
docker container stop <container-id>                       # Stop container
docker container rm <container-id>                         # Delete container
docker container prune                                     # Remove all stopped containers
docker images --filter "dangling=true"                     # Show untagged images
docker image prune --filter="dangling=true"                # Delete untagged images
docker image prune --all                                   # Remove all unused images
docker system prune                                        # Remove everything not used
docker rmi <img-id>                                        # Delete image
docker run --publish 8000:8000 <container-tag>             # Run container and expose <host:container> ports
docker run -d <container-tag>                              # Run in detached mode
docker exec -it <container-id> bash                        # Attach to a running container in interactive mode
                                                           # -it are two parameters: -i(--interactive) and -t(--tty):
docker run --rm -it <container-tag>                        # Run container in interactive mode and remove it when it exits
docker run --entrypoint=<path>                             # Run container and override CMD
docker build --f <dockerfile> --tag <repo/img-name> <path> # Build image and tag it
docker build --no-cache --f <dockerfile>                   # Force image rebuild from scratch
```

## Scan image

```text
docker pull goodwithtech/dockle:latest
docker run --rm goodwithtech/dockle:latest <img-name>
```
