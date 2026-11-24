# HomeOS support

This is an independently maintained, AI-assisted project. Bug reports, reproducible examples and polite technical suggestions are welcome. Fix and response times are not guaranteed.

## Troubleshooting

| Problem | First check |
| --- | --- |
| Docker image won't pull | Check the image tag in `.env` and that the Docker host can reach `ghcr.io` |
| HomeOS page won't load | `docker compose ps`, port binding, firewall and trusted-LAN access |
| First-run setup needs a token | `docker compose logs --tail=100 homeos` or the Unraid container log |
| Integration won't connect | Address reachable from container, credentials, API permissions and TLS certificate |
| Data disappears after a reinstall | Check whether existing `/config` and MyFiles volumes were preserved |
| An integration is slow or times out | Check the remote service API and logs; don't paste secret-bearing logs publicly |

## Bugs and ideas

Open [GitHub Issues](https://github.com/ozkernel/homeos/issues/new/choose) and choose the right form:

- **Bug report:** Tell us what went wrong, your HomeOS version, steps to reproduce and any **redacted** logs.
- **Idea / feature request:** Suggest an integration, feature or improvement and explain how it would help.

HomeOS uses Issues for both bug reports and ideas; there is no Discussions section.

Do **not** upload `.env`, passwords, tokens, full system dumps, internal-only URLs or personal information.

For security concerns, follow [SECURITY.md](SECURITY.md) instead of creating a public issue.

[Install](INSTALLATION.md) · [Configuration](CONFIGURATION.md)
