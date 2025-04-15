# Dockge

## Overview

Dockge is a web-based Docker Compose stack management tool. It provides a simple
interface to manage all your Docker Compose services in one place.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `PGID` | Group ID to run as | Yes |
| `PUID` | User ID to run as | Yes |
| `UMASK` | File permission mask | No |
| `DOCKGE_USERNAME` | Admin username (if auth enabled) | No |
| `DOCKGE_PASSWORD` | Admin password (if auth enabled) | No |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_FOLDER_STACKS` | Directory containing stack definitions | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_DATA}:/app/data`: Persistent Dockge data
- `${SERVICE_FOLDER_STACKS}:/opt/stacks`: Access to Docker Compose stacks
- `/var/run/docker.sock`: Access to Docker socket

## Ports

- `5001`: Web interface

## Notes

- Dockge requires access to the Docker socket, which gives it full control over
  Docker. Make sure to secure access to the Dockge interface.
- If you enable authentication, use a strong password.

## Links

- [Documentation](https://github.com/louislam/dockge)
- [GitHub Repository](https://github.com/louislam/dockge)
- [Docker Hub](https://hub.docker.com/r/louislam/dockge)
