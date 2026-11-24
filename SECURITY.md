# Security policy and reporting

HomeOS may hold API credentials for services on your homelab network. Keep those credentials secure and grant only the permissions you need.

- Install HomeOS on a **trusted LAN or VPN**. Avoid direct internet exposure of its HTTP port.
- Use an appropriately secured HTTPS proxy for remote access and limit trusted proxy addresses.
- Back up HomeOS configuration (including encryption keys) and MyFiles together.
- Never share unredacted `.env` files, passwords, API keys, setup/recovery tokens, cookies or sensitive logs.
- Review release notes and install official versioned Docker images.

## Privately report a vulnerability

Please **do not publish vulnerability details in a GitHub Issue**.

Use [GitHub private vulnerability reporting](https://github.com/ozkernel/homeos/security/advisories/new) **if it is enabled**. Otherwise open an issue requesting a private reporting contact **without including exploit details**.

This public repository contains installer materials and docs, not the application's private source code. Security-sensitive build and dependency checks take place separately.
