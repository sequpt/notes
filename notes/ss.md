# ss

Utility to investigate sockets

- Website: <https://wiki.linuxfoundation.org/networking/iproute2>
- Code:
  - <https://git.kernel.org/pub/scm/network/iproute2/iproute2.git>
  - <https://github.com/shemminger/iproute2>

## Installation

`sudo apt-get install iproute2`

## Usage

### Short form

```text
ss -lnpt #1 Print informations about processes listening on sockets using TCP
```

### Long form

```text
ss --listenting --numeric --process --tcp #1
```
