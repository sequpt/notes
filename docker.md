# docker

Application container

- Website: <https://www.docker.com/>
- Doc: <https://docs.docker.com/>
- Repo: <https://github.com/moby/moby>

## Installation

### Rootful Debian 11+

```text
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
    | sudo tee /etc/apt/sources.list.d/docker.list \
    > /dev/null
sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### Rootless Debian 11+

```text
sudo apt-get install \
    ca-certificates \
    curl \
    dbus-user-session \
    fuse-overlayfs \
    gnupg \
    lsb-release \
    slirp4netns \
    uidmap
curl -fsSL https://get.docker.com/rootless | sh
systemctl --user start docker
systemctl --user enable docker
sudo loginctl enable-linger $(whoami)
```

```text
# Add to `~/.bashrc`
export PATH="$PATH:$HOME/bin"
export DOCKER_HOST="unix://$XDG_RUNTIME_DIR/docker.sock"
```

## Usage

```text
docker container stop <container-id>          : Stop container
docker container rm <container-id>            : Delete container
docker container prune                        : Remove all stopped containers
docker images --filter "dangling=true"        : Show untagged images
docker image prune --filter="dangling=true"   : Delete untagged images
docker rmi <img-id>                           : Delete image
docker run --publish 8000:8000 <container-tag>: Run container and expose <host:container> ports
docker run -d <container-tag>                 : Run in detached mode
docker exec -it <container-id> bash           : Attach to a running container in interactive mode
                                              : -it are two parameters: -i(--interactive) and -t(--tty):
docker run --rm -it <container-tag>           : Run container in in interactive mode and remove it when it exits
```

## Scan image

```text
docker pull goodwithtech/dockle:latest
docker run --rm goodwithtech/dockle:latest <img-name>
```
