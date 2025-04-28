# Syncthing

## Overview

Syncthing is a continuous file synchronization program that synchronizes files
between two or more computers in real time. It's secure, decentralized, and
open-source. Unlike cloud storage services, your data is stored only on your
devices, giving you complete control and privacy.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `PGID` | Group ID for permissions | Yes |
| `PUID` | User ID for permissions | Yes |
| `SERVICE_FOLDER_CONFIG` | User ID for permissions | Yes |
| `SERVICE_FOLDER_DATA` | User ID for permissions | Yes |
| `SERVICE_PORT` | Port for web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_CONFIG}:/config`: Contains Syncthing's configuration
- `${SERVICE_FOLDER_DATA}:/data`: The default sync directory (you can add more)

## Ports

- `8384`: Web interface
- `22000`: TCP file transfer port
- `21027`: UDP discovery port (broadcast)

## Security Considerations

For optimal security:

1. **Set a strong password** for the web interface
2. **Restrict access** to the web interface:
   - In the GUI settings, change "GUI Listen Address" to `127.0.0.1:8384` to
     restrict it to local access only
   - Use a reverse proxy with authentication for remote access

1. **Use secure connections**:
   - Enable HTTPS in the GUI settings
   - Use relay servers only when necessary

## Folder Sharing

To set up synchronized folders:

1. Click "Add Folder" in the web interface
2. Set a folder ID (a short name, like "Documents")
3. Choose the directory path on your server
4. Select which devices to share with
5. Configure versioning if desired (to keep deleted/changed files)
6. Click "Save"

You'll need to accept the folder on the other device(s).

## Recommended Sync Strategies

For optimal performance:

1. **Documents & Small Files**:
   - Enable "Watch for Changes" for immediate sync
   - Use versioning to recover from accidental deletions

2. **Photos & Media**:
   - Consider "Send Only" from phones/cameras to server
   - Use "Ignore Permissions" for media libraries

3. **Large Files/Backups**:
   - Disable "Watch for Changes" to reduce resource usage
   - Set appropriate scan intervals (e.g., daily)

## Mobile Devices

Syncthing works well with mobile devices:

- **Android**: [Syncthing-Fork](https://play.google.com/store/apps/details?id=com.github.catfriend1.syncthingandroid)
- **iOS**: [MobiusSync](https://apps.apple.com/app/mobius-sync/id1539203216) (third-party client)

## Advanced Topics

### Selective Sync

You can use ignore patterns to exclude files from synchronization:
- In the folder settings, go to "Ignore Patterns"
- Add patterns like `*.tmp`, `node_modules/`, etc.

### Custom Relay & Discovery

For better performance or privacy, you can:
- Disable global discovery in the settings
- Configure direct connections between your devices
- Set up your own relay server if needed

## Links

- [Official Website](https://syncthing.net/)
- [Documentation](https://docs.syncthing.net/)
- [GitHub Repository](https://github.com/syncthing/syncthing)
- [Docker Hub](https://hub.docker.com/r/linuxserver/syncthing)
- [Community Forum](https://forum.syncthing.net/)
