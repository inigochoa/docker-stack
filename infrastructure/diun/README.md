# Diun

## Overview

Diun (Docker Image Update Notifier) is a service that monitors Docker images and
notifies you when new versions are available. Unlike Watchtower, Diun only sends
notifications and does not automatically update your containers.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|---------|----------|
| `DIUN_PROVIDERS_DOCKER` | Enable Docker provider | Yes |
| `DIUN_WATCH_SCHEDULE` | Cron schedule for checking updates | Yes |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `TZ` | Timezone | Yes |

## Container Monitoring

With `DIUN_PROVIDERS_DOCKER_WATCHBYDEFAULT=false` (recommended), Diun will only
monitor containers with specific labels:

```yaml
labels:
  - diun.enable=true
```

You can add additional controls with more labels:
```yaml
labels:
  - diun.enable=true
  - diun.regopt=somekey
  - diun.watch_repo=true  # Watch entire repository for new tags
```

## Notification Methods

Diun supports multiple notification methods. Check the
[official documentation](https://crazymax.dev/diun/config/notifications/) for
configuration details.

## Update Schedule

The default schedule is set to run at midnight every day. You can customize this
using the cron format:

```
DIUN_WATCH_SCHEDULE=0 0 * * *
```

Format: `minute hour day month weekday`

Examples:
- Every night at midnight: `0 0 * * *`
- Every Sunday at 2 AM: `0 2 * * 0`
- Every 6 hours: `0 */6 * * *`

## Volumes

- `/opt/data/diun/data`: Persistent Diun data
- `/var/run/docker.sock`: Access to Docker socket (required)

## Security Considerations

- Diun requires access to the Docker socket, which gives it read access to your
  Docker environment
- It has a smaller attack surface than Watchtower since it doesn't perform
  container updates

## Links

- [Diun GitHub Repository](https://github.com/crazy-max/diun)
- [Official Documentation](https://crazymax.dev/diun/)
- [Docker Hub](https://hub.docker.com/r/crazymax/diun/)
