# gpg

GNU Privacy Guard

- Website: <https://gnupg.org>
- Doc:     <https://gnupg.org/documentation/index.html>
- Source:  <https://git.gnupg.org/cgi-bin/gitweb.cgi>

## Installation

### Debian

`sudo apt-get install gpg`

- GUI
  - seahorse: `sudo apt-get install seahorse`

## Usage

```text
pub: public primary key
sec: secret primary key
sig: signature
ssb: secret secondary key
sub: Public secondary key
uid: user id
```

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
```
