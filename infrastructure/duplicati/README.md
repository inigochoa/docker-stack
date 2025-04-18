# Duplicati

## Overview

Duplicati is a free, open-source backup client that securely stores encrypted,
incremental, compressed backups on cloud storage services and remote file
servers. It works with various protocols and services like FTP, SSH, WebDAV,
Amazon S3, OneDrive, Google Drive, etc.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `PGID` | Group ID | Yes |
| `PUID` | User ID | Yes |
| `SERVICE_FOLDER_BACKUPS` | Local backups folder | Yes |
| `SERVICE_FOLDER_CONFIG` | Duplicati config folder | Yes |
| `SERVICE_FOLDER_SOURCE` | Backups source folder | Yes |
| `SERVICE_PORT` | Port for web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_BACKUPS}:/backups`: Default local backup destination
- `${SERVICE_FOLDER_CONFIG}:/config`: Duplicati configuration and database
- `/opt/data:/source/data:ro`: Read-only access to the data directory to back up
  all service data

## Links

- [Duplicati Documentation](https://duplicati.readthedocs.io/)
- [Duplicati GitHub Repository](https://github.com/duplicati/duplicati)
- [Backup Strategies Guide](https://duplicati.readthedocs.io/en/latest/appendix-c-backup-strategies/)
