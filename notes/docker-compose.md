# docker-composse

Run multi-container Docker applications

- Website: <https://docs.docker.com/compose/>
- Doc: <https://www.openssh.com/manual.html>
- Repo: <https://github.com/docker/compose>

## Installation

- Debian: `sudo apt-get install --no-install-recommends docker-compose`
- Binaries: <https://github.com/docker/compose/releases>

## Usage

```text
# Build all services
docker-compose build
# Build a specific service
docker-compose build <service>
# Build multiples services
docker-compose build <service0> <service1>
# Build all services with path to `docker-compose.yml`
docker-compose -f <path> build
# Build all services with a `.env` file
docker-compose --env-file <path> build
# Start all service
docker-compose up
# Start a specific service
docker-compose up <service>
# Start multiples services
docker-compose up <service0> <service1>
# Start all service in the background
docker-compose up -d
# Start docker-compose with profiles from the 'profiles' keys
docker-compose --profile <profile0> --profile <profile1> up
# Stop services
docker-compose down
```
