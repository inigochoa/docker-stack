# Docker Stack

A complete self-hosted infrastructure and service deployment using Docker
Compose.

## Overview

This repository contains all the necessary configurations to deploy a complete
stack of self-hosted services managed by Docker Compose. It's organized into
infrastructure components and application services.

## Directory Structure

```
docker-stack/
├── infrastructure/   # Core infrastructure services
└── services/         # Application services
```

## Requirements

- Docker Engine (version 20.10+)
- Docker Compose V2
- Git
- At least 4GB RAM (recommended 8GB+)
- Sufficient disk space for your services (recommended 100GB+)

## Data Storage

All service data is stored in `/opt/data/[service-name]`. Make sure this
directory exists and has appropriate permissions.

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/inigochoa/docker-stack.git
   cd docker-stack
   ```

2. Set up environment files:
   ```bash
   ./scripts/create-env-files.sh
   ```

3. Edit the generated `.env` files with your specific configuration values.

4. Deploy the infrastructure first:
   ```bash
   cd infrastructure/dockge
   docker compose up -d
   ```

5. Once Dockge is running, you can use it to deploy the rest of the services or
   continue with manual deployment.

## Services

### Infrastructure

- **Cloudflared**: Cloudflare Tunnel for secure remote access.
- **Diun**: Monitor Docker images.
- **Dockge**: Docker Compose stack management UI.
- **Duplicati**: Backup solution for your data.

### Applications

- **Baïkal**: CalDAV+CardDAV server.
- **FreshRSS**: RSS feed aggregator.
- **Joplin**: An open source note-taking app.
- **Syncthing**: Continuous file synchronization program.
- **Vaultwarden**: Password manager (Bitwarden compatible).
- **Wallabag**: Save and classify articles from the web.
- **Wallos**: Subscription tracker.
- **Yamtrack**: Media tracker.

## Maintenance

### Backups

All data is stored in `/opt/data/`. Configure Duplicati to back up this
directory.

```bash
./scripts/backup.sh
```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for
details.
