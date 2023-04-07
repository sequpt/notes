# gpg

GNU Privacy Guard

- Website: <https://gnupg.org/>
- Repo: <https://git.gnupg.org/cgi-bin/gitweb.cgi>

## Installation

- Debian: `sudo apt-get install gpg`

## Usage

```text
# Generate a pair of public/private keys
gpg --full-gen-key
# List public keys
gpg --list-keys --keyid-format=long
# List secret keys
gpg --list-secret-keys --keyid-format=long
# Show a specific private key
gpg --keyid-format=long -k <PUBLIC_PRIMARY_KEY|PUBLIB_SECONDARY_KEY>
# List signatures
gpg --list-signatures
# List fingerprints
gpg --list-signatures
# Export public key
gpg --output public.pgp --armor --export <PUBLIC_PRIMARY_KEY>
# Restart gpg-agent
gpgconf --kill gpg-agent
```

```text
pub: public primary key
sec: secret primary key
sig: signature
ssb: secret secondary key
sub: Public secondary key
uid: user id
```
