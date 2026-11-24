# Configure HomeOS

HomeOS starts with **Demo Mode** sample data on a new installation. After administrator setup, switch to **Live Mode** and add only the integrations you want.

## Integrations

Navigate to the HomeOS integration settings. Add a server address and any required API credentials, test the connection, then save. Supported services include Unraid, Proxmox VE, Proxmox Backup Server, Plex, Jellyfin, Seerr, Sonarr, Radarr, Lidarr, Bazarr, Prowlarr, qBittorrent, SABnzbd, UniFi and AdGuard Home.

Use the **minimum permissions** needed. Avoid giving integrations full administrator rights unless a management feature explicitly requires them. Servers should be reachable from the HomeOS **container**, not only from your computer.

## Docker settings

Edit your **private local** `.env` file, not `.env.example` in the public repository.

| Setting | Purpose |
| --- | --- |
| `HOMEOS_IMAGE` | Official Docker image (default `ghcr.io/ozkernel/homeos:1.0.0`) |
| `HOMEOS_BIND` | `127.0.0.1` for host-only or `0.0.0.0` for trusted LAN |
| `HOMEOS_HOST_PORT` | Docker host port (default `3080`) |
| `HOMEOS_DEMO` | Initial Demo Mode for a new database |
| `ADMIN_USERNAME`, `ADMIN_PASSWORD` | Optional first-run bootstrap credentials; leave blank for interactive setup |
| `TZ` | Your IANA time zone |
| `MYFILES_STORAGE_PATH` | Saved files path inside container; keep consistent with volume mapping |
| `HOMEOS_HTTPS_ONLY` | Enable only when correct HTTPS proxy setup is in place |
| `HOMEOS_TRUSTED_PROXIES` | Trusted reverse-proxy IPs/CIDRs, if used |

HomeOS stores state under `/config` and files under `/app/data/myfiles`. Back up **both** locations, especially the database and encryption key. Switching to new empty volumes can make existing data appear missing.

[Installation](INSTALLATION.md) · [Security](SECURITY.md) · [Support](SUPPORT.md)
