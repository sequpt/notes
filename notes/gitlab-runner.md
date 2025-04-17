# GitLab Runner

- Doc: <https://docs.gitlab.com/runner/>

```text
# Install runner
docker pull gitlab/gitlab-runner:latest

# Create volume for configuration data
# Path: `$XDG_DATA_HOME/docker/volumes/gitlab-runner-<id>-config/_data/config.toml`
docker volume create gitlab-runner-<id>-config

# Register runner
# <url> = https://gitlab.com for GitLab
# <url> and <token> are found in Settings->CI/CD->Runners
docker run --rm \
  -v gitlab-runner-<id>-config:/etc/gitlab-runner \
  gitlab/gitlab-runner:latest register \
    --non-interactive \
    --name "gitlab-runner-<id>" \
    --limit 6 \
    --request-concurrency 6 \
    --url "https://gitlab.com" \
    --token "<token>" \
    --executor "docker" \
    --env "FF_NETWORK_PER_BUILD=1" \
    --env "FF_POSIXLY_CORRECT_ESCAPES=1" \
    --docker-image "alpine:latest" \
    --docker-pull-policy "if-not-present"

# Start runner with associated volume
docker run -d \
  --name gitlab-runner-<id> \
  -v $XDG_RUNTIME_DIR/docker.sock:/var/run/docker.sock \
  -v gitlab-runner-<id>-config:/etc/gitlab-runner \
  gitlab/gitlab-runner:latest

# Restart runner after updating `config.toml`
docker restart gitlab-runner-<id>

# Upgrade runner
docker stop gitlab-runner-<id> && docker rm gitlab-runner-<id>
docker run -d --name gitlab-runner-<id> -v gitlab-runner-<id>-config:/etc/gitlab-runner gitlab/gitlab-runner:latest

# Print runner logs to terminal
docker logs gitlab-runner-<id>

# Print runner help
docker run --rm gitlab/gitlab-runner:latest -h
```
