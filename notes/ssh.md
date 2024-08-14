# ssh

OpenSSH remote login client.

- Homepage: <https://www.openssh.com/>
- Doc: <https://www.openssh.com/manual.html>
- Repo: <https://github.com/openssh/openssh-portable>

## Installation

- Debian package: `openssh-client`

## Usage

```text
# Create a public/private key pair without hostname@username comment in public key
# and without passphrase
ssh-keygen -f ~/.ssh/<filename> -t ed25519 -C "" -N ""

# Send public key to server
ssh-copy-id -i ~/.ssh/<private_key_file> <user>@<host>

# Add key to agent
ssh-add ~/.ssh/<private_key_file>

# Files and directories permission
~/.ssh/           : 700 (drwx------)
Public key (*.pub): 644 (-rw-r--r--)
~/.ssh/config     : 600 (-rw-------)
Private key       : 600 (-rw-------)
```
