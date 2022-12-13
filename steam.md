# steam

Video game digital distribution service

- Website: <https://store.steampowered.com/>
- Proton: [repo](https://github.com/ValveSoftware/Proton)/[doc](https://github.com/ValveSoftware/Proton/wiki)
- steamcmd: <https://developer.valvesoftware.com/wiki/SteamCMD>

## Installation

### steam

- Debian: `sudo dpkg --add-architecture i386 && sudo apt-get install steam`
- Binaries: <https://cdn.akamai.steamstatic.com/client/installer/steam.deb>

### steamcmd

- Debian: `sudo dpkg --add-architecture i386 && sudo apt-get install steamcmd`
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
