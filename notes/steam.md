# steam

Video game digital distribution service.

- Homepage: <https://store.steampowered.com/>
- proton
  - Doc: <https://github.com/ValveSoftware/Proton/wiki>
  - Repo: <https://github.com/ValveSoftware/Proton>
- steamcmd
  - Doc: <https://developer.valvesoftware.com/wiki/SteamCMD>

## Installation

### steam

- Debian package: `steam`
  - `dpkg --add-architecture i386 && apt-get install steam`
- Binaries: <https://cdn.akamai.steamstatic.com/client/installer/steam.deb>

### steamcmd

- Debian package: `steamcmd`
  - `dpkg --add-architecture i386 && apt-get install steamcmd`
- Binaries: <http://media.steampowered.com/installer/steamcmd_linux.tar.gz>

## Usage

```text
# Run steamcmd
steamcmd
# Install game
force_install_dir <path>
login <username>
app_update <appid> validate
# Install Windows game on Linux
@sSteamCmdForcePlatformType windows
force_install_dir <path>
login <username>
app_update <appid> validate
```
