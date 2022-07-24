# GitLab

## Runner

- Doc: <https://docs.gitlab.com/runner/>

```text
# Install runner
sudo docker pull gitlab/gitlab-runner:alpine

# Create volume for configuration data
# Set <ID> to a unique id identifying a site/repository running gitlab-runner
# Volume is stored in `/var/lib/docker/volumes/gitlab-runner-config-<ID>/_data/config.toml`
sudo docker volume create gitlab-runner-config-<ID>

# Start runner with associated volume
sudo docker run -d --name gitlab-runner-<ID> -v gitlab-runner-config-<ID>:/etc/gitlab-runner gitlab/gitlab-runner:alpine

# Register runner
# <URL> = https://gitlab.com for GitLab
# <URL> and <TOKEN> are found in Settings->CI/CD->Runners
# <IMG-NAME> is the default image to use if none is provided in `.gitlab-ci.yml`
sudo docker run --rm -it -v gitlab-runner-config-<ID>:/etc/gitlab-runner gitlab/gitlab-runner:alpine register \
    --non-interactive \
    --url "<URL>" \
    --registration-token "<TOKEN>" \
    --executor "docker" \
    --docker-image "<IMG-NAME>" \
    --docker-pull-policy "if-not-present"

# Restart runner after updating `config.toml`
sudo docker restart gitlab-runner-<ID>

# Upgrade runner
sudo docker stop gitlab-runner-<ID> && sudo docker rm gitlab-runner-<ID>
sudo docker run -d --name gitlab-runner-<ID> -v gitlab-runner-config-<ID>:/etc/gitlab-runner gitlab/gitlab-runner:alpine

# Print runner logs to terminal
sudo docker logs gitlab-runner-<ID>

# Print runner help
sudo docker run --rm gitlab/gitlab-runner:alpine -h

```

## Build and push docker images to registry

```text
# Build image
sudo docker build -t registry.gitlab.com/<namespace>/<project>/<img-name> -f <dockerfile> <path>
sudo docker build -t registry.gitlab.com/callback/tool-config/debian-gcc-10 -f debian-gcc-10.dockerfile .

# Login to registry (insecure)
sudo docker login registry.gitlab.com -u <user> -p <password>

# Login to registry (secure)
# Enter password when prompted
sudo docker login registry.gitlab.com -u <user>

# Push image to gitlab
sudo docker push registry.gitlab.com/<namespace>/<project>/<img-name>
sudo docker push registry.gitlab.com/callback/tool-config/debian-gcc-10

# Logout when done
sudo docker logout registry.gitlab.com
```
