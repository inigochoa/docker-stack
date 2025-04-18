# Vaultwarden

## Overview

Vaultwarden is an unofficial Bitwarden server implementation written in Rust. It
provides password management services compatible with Bitwarden clients.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `ADMIN_RATELIMIT_*` | Admin login limits | No |
| `ADMIN_TOKEN` | Admin panel access token | Yes |
| `DOMAIN` | Public domain name | Yes |
| `EMERGENCY_ACCESS_ALLOWED` | Allow emergency access | No |
| `INVITATIONS_ALLOWED` | Allow registration invitations | No |
| `LOGIN_RATELIMIT_*` | Login limits | No |
| `PUSH_*` | Enable push for the app | No |
| `SENDS_ALLOWED` | Allow sends | No |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SIGNUPS_ALLOWED` | Allow new user registrations | No |
| `TZ` | Timezone | No |
| `WEB_VAULT_ENABLED` | Enable the web vault interface | No |

## Volumes

- `${SERVICE_FOLDER_DATA}:/data`: All persistent data

## Links

- [Official GitHub Repository](https://github.com/dani-garcia/vaultwarden)
- [Vaultwarden Wiki](https://github.com/dani-garcia/vaultwarden/wiki)
- [Bitwarden Website](https://bitwarden.com/)
