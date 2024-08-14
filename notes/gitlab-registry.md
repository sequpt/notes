# Gitlab Registry

## Container Registry

### Build and push docker images to registry

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
