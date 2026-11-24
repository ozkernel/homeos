# Install HomeOS v1.0.0

HomeOS runs as a **Linux amd64 Docker image**, not from the files in this repository. The image reference for this version is `ghcr.io/ozkernel/homeos:1.0.0`. See [HomeOS Releases](https://github.com/ozkernel/homeos/releases) for release notes.

## Docker Compose

1. Install Docker Engine + Compose v2, or Docker Desktop in Linux-container mode.
2. Download this repository and extract it (or clone it). Open a terminal in the folder containing `docker-compose.yml`.
3. Copy `.env.example` to `.env`. Leave `ADMIN_USERNAME` and `ADMIN_PASSWORD` empty for interactive first-run setup.
4. Run:

```sh
docker compose config --quiet
docker compose pull
docker compose up -d
docker compose ps
```

5. Open `http://127.0.0.1:3080` on the Docker host and complete the first-run setup. If prompted for a one-time setup token, inspect `docker compose logs --tail=100 homeos` and keep it private.

The default bind is `127.0.0.1` so the service is only reachable from its Docker host. For **trusted LAN** access, set `HOMEOS_BIND=0.0.0.0` in your private `.env`, then run `docker compose up -d` again and visit `http://YOUR-DOCKER-HOST-IP:3080`.

**Never forward the plain HTTP port directly to the internet.** Prefer a VPN or a properly secured HTTPS reverse proxy for remote use.

## Unraid

Open **Unraid → Terminal** and run:

```sh
mkdir -p /boot/config/plugins/dockerMan/templates-user
curl -fL https://raw.githubusercontent.com/ozkernel/homeos/main/templates/homeos.xml -o /boot/config/plugins/dockerMan/templates-user/my-HomeOS.xml
```

Then choose **Docker → Add Container → HomeOS** from your user templates, review the settings and apply it.

| Option | Initial value |
| --- | --- |
| Image | `ghcr.io/ozkernel/homeos:latest` |
| Web UI port | `3080` |
| Configuration storage | `/mnt/user/appdata/homeos/config` → `/config` |
| MyFiles storage | `/mnt/user/appdata/homeos/myfiles` → `/app/data/myfiles` |
| Recommended access | Trusted LAN or VPN |

If the template isn't listed, return to the Docker Add Container page and check User Templates, or install the template manually from `templates/homeos.xml`.

Open `http://YOUR-UNRAID-IP:3080`, review any setup-token instructions in the HomeOS container logs, and complete account creation.

**Unraid Community Applications:** This is a manual user template; appearing in Community Applications requires a separate submission and acceptance.

## Keep your data safe

HomeOS needs persistent storage for **both** the database/encryption key (`/config`) and saved files (`/app/data/myfiles`). Docker Compose uses the `homeos_config` and `homeos_myfiles` named volumes unless you deliberately choose a different mapping.

Back up both before changing container paths or updating. Don't delete volumes or use `docker compose down -v` on an existing installation. To update, point `HOMEOS_IMAGE` at the new release tag, then run `docker compose pull && docker compose up -d`. On Unraid, use **Check for Updates** on the Docker page.

[Configuration](CONFIGURATION.md) · [Troubleshooting](SUPPORT.md) · [Security](SECURITY.md)
