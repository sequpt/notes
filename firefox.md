# firefox

Web browser

- Website: <https://www.mozilla.org/en-US/firefox/new/>
- Repo: <https://hg.mozilla.org/mozilla-central>

## Installation command

- Debian: `sudo apt-get install firefox-esr`

## Binaries

- Linux: <https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US>

## Profile location

- Debian: `$HOME/.mozilla/firefox/`

### Keep

```text
bookmarkbackups       : Backups directory for bookmarks
cert9.db              : Security/SSL certificate settings
containers.json       : Settings for Container Tab feature
content-prefs.sqlite  : Site preferences
extension             : Store extensions *.xpi files
favicons.sqlite       : Website icons for bookmarks
handlers.json         : Download actions(according to file type)
permissions.sqlite    : Permission database for cookies, pop-up blocking, image loading and add-ons installation
persdict.dat          : Personal dictionary(user-added words)
pkcs11.txt            : Security module configuration
places.sqlite         : Bookmarks, browsing and downloads history[nuke the last two]
prefs.js              : User preferences
search.json.mozlz4    : Search engines(user-installed)
storage-sync-v2.sqlite: Extensions configuration(can contain browsing history)
user.js               : User preferences(overrides `prefs.js` if present)
xulstore.json         : Toolbar customization
```

### Discard

```text
.parentlock                 : Lock file indicating the profile is in use
SiteSecurityServiceState.txt: HSTS "supercookie"[set to read-only]
cookies.sqlite              : Cookies
cookies.sqlite-wal          : SQL Write-Ahead Logging
crashes                     : ?
datareporting               : ?
favicons.sqlite-wal         : SQL Write-Ahead Logging
formhistory.sqlite          : Autocomplete history(search bars and forms)
key4.db                     : Passwords
logins.json                 : Passwords
times.json                  : Profile creation date
webappsstore.sqlite         : Websites DOM storage
```

### Don't know

```text
AlternateServices.txt       : ?
ClientAuthRememberList.txt  : ?
addon.json                  : Addon repository info
addonStartup.json.lz4       : ?
broadcast-listeners.json    : ?
cert_override.txt           : Certificate exceptions specified by the user
compatibility.ini           : Stores version and path of the application this profile was last used with
enumerate_devices.txt       : ?
extension-preferences.json  : ?
extension-settings.json     : ?
extensions.json             : Information about installed extensions
minidumps                   : ?
places.sqlite-wal           : SQL Write-Ahead Logging
protections.sqlite          : ?(empty on creation)
saved-telemetry-pings       : ?
security_state              : CRLite
sessionCheckpoints.json     : Store profile state after every notification
sessionstore-backups        : Session backups
sessionstore.jsonlz4        : Stored session(current windows and tabs open)
settings                    : ?
storage-sync-v2.sqlite-shm  : SQL Wal-Index(doesn't contain any database content)
storage-sync-v2.sqlite-wal  : SQL Write-Ahead Logging(WAL)
storage.sqlite              : ?(empty on creation)
weave                       : ?
```
