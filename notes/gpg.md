# gpg

GNU Privacy Guard.

- Homepage: <https://gnupg.org>
- Doc: <https://gnupg.org/documentation/index.html>
- Repo: <https://git.gnupg.org/cgi-bin/gitweb.cgi>

## Installation

- Debian package: `gpg`
  - GUI: `seahorse`

## Usage

```text
gpg --full-gen-key                             # Generate a pair of public/private keys
gpg --list-keys                                # List public keys
gpg --list-keys --keyid-format=long            # List public keys and show key-id
gpg --list-secret-keys --keyid-format=long     # List secret keys and show key-id
gpg --keyid-format=long -k <pub|sub>           # Show a specific private key
gpg --list-signatures                          # List signatures
gpg --list-signatures                          # List fingerprints
gpg --output public.pgp --armor --export <pub> # Export public key
gpg --import <path>                            # Import key
gpgconf --kill gpg-agent                       # Restart gpg-agent
echo "<key-id>:<trust-level>:" \               # Set key trust level
  | gpg --import-ownertrust
gpg --delete-key <key-id>                      # Delete public key(secret key must be deleted first if it exists)
gpg --delete-secret-key <key-id>               # Delete secret key
```

## Misc info

### Abbreviations

```text
pub: public primary key fingerprint
sec: secret primary key
sig: signature/key id
ssb: secret secondary/sub key
sub: public secondary/sub key
uid: user id
```

### Trust levels

```text
2: I don't know or won't say [ unknown]
3: I do NOT trust            [ unknown]
4: I trust marginally        [ unknown]
5: I trust fully             [ unknown]
6: I trust ultimately        [ultimate]
```
