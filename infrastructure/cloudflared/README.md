# Cloudflared

## Overview

Cloudflared is the client for Cloudflare Tunnel, a service that creates secure
tunnels from your infrastructure to the Cloudflare network without opening
inbound ports.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `SERVICE_FOLDER_DATA` | Data folder | Yes |
| `TUNNEL_TOKEN` | Tunnel Token | Yes |
| `TZ` | Timezone | Yes |

## Notes

- Make sure your Cloudflare account has the necessary permissions
- Tunnels can only be created by users with the Administrator role
- If you're routing to other Docker services, ensure they're on the same Docker
  network or properly addressable

## Links

- [Cloudflare Tunnel Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)
- [Cloudflared GitHub Repository](https://github.com/cloudflare/cloudflared)
- [Cloudflare Zero Trust](https://www.cloudflare.com/products/zero-trust/)
