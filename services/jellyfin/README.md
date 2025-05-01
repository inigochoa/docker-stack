# Jellyfin

## Overview

Jellyfin is an open-source media server that lets you organize, manage, and
stream your media collection (movies, TV shows, music, photos) to any device.
It's a free alternative to services like Plex and Emby, with no premium features
or subscriptions required.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Default | Required |
|----------|-------------|---------|----------|
| `JELLYFIN_PORT` | Port for web interface | `8096` | Yes |
| `JELLYFIN_HTTPS_PORT` | Port for HTTPS access | `8920` | No |
| `JELLYFIN_UDP_PORT` | Port for service discovery | `7359` | No |
| `PUID` | User ID for permissions | `1000` | Yes |
| `PGID` | Group ID for permissions | `1000` | Yes |
| `TZ` | Timezone | `Europe/Madrid` | Yes |
| `JELLYFIN_CACHE_DIR` | Transcoding cache location | `/opt/data/jellyfin/cache` | Yes |
| `JELLYFIN_CONFIG_DIR` | Configuration directory | `/opt/data/jellyfin/config` | Yes |
| `JELLYFIN_MEDIA_DIR` | Main media directory | `/opt/data/jellyfin/media` | Yes |
| `JELLYFIN_MEMORY_LIMIT` | Memory limit | `2G` | No |
| `JELLYFIN_CPU_LIMIT` | CPU limit | `2.0` | No |
| `WATCHTOWER_UPDATES` | Enable automatic updates | `true` | No |

## Volumes

- `/opt/data/jellyfin/config`: Configuration files
- `/opt/data/jellyfin/cache`: Transcoding cache
- `/opt/data/jellyfin/media`: Your media library (movies, shows, music, etc.)

## Ports

- `8096`: Web interface (HTTP)
- `7359`: UDP for local network service discovery

## Hardware Acceleration

The default configuration supports hardware acceleration. If you have:

- **Intel GPU**: Enables VAAPI acceleration (make sure to have `/dev/dri`
  devices mounted)
- **NVIDIA GPU**: Uncomment the GPU settings in the compose file to enable NVENC
  acceleration

## Initial Setup

1. Deploy Jellyfin:
   ```bash
   docker compose up -d
   ```

2. Access the web interface at:
   ```
   http://your-server:8096
   ```

3. Follow the setup wizard:
   - Create your admin user
   - Set up your media libraries
   - Configure preferred display settings

## Media Library Organization

For best results, organize your media following these conventions:

### Movies

```
/opt/data/jellyfin/media/Movies/
├── Movie Title (Year)/
│   ├── Movie Title (Year).mp4
│   └── subtitle.srt
├── Another Movie (Year)/
│   └── Another Movie (Year).mkv
```

### TV Shows

```
/opt/data/jellyfin/media/TV/
├── Show Name/
│   ├── Season 01/
│   │   ├── Show Name - S01E01.mp4
│   │   └── Show Name - S01E02.mp4
│   └── Season 02/
│       └── ...
├── Another Show/
│   └── ...
```

### Music

```
/opt/data/jellyfin/media/Music/
├── Artist/
│   ├── Album (Year)/
│   │   ├── 01 - Track.mp3
│   │   └── 02 - Track.mp3
│   └── Another Album (Year)/
│       └── ...
```

## Plugins and Extensions

Jellyfin supports plugins for additional functionality:

1. In the web interface, go to "Dashboard" → "Plugins"
2. Browse available plugins such as:
   - Fanart (enhanced artwork)
   - Intro Skip
   - Metadata enhancers
   - Theme songs

## Client Apps

Jellyfin has clients for many platforms:

- **Web**: Built-in web interface
- **Android/iOS**: Official mobile apps
- **TV**: Android TV, Fire TV, Apple TV, Roku apps
- **Desktop**: Jellyfin Media Player (Windows, macOS, Linux)
- **Kodi**: Jellyfin for Kodi add-on

## Accessing via Cloudflare Tunnel

If you want to access Jellyfin remotely via Cloudflare Tunnel, add the following to your Cloudflared configuration:

```yaml
# In your cloudflared config.yaml
ingress:
  # Jellyfin
  - hostname: media.yourdomain.com
    service: http://jellyfin:8096
  # Other services...
```

**Note**: For optimal streaming performance outside your network, consider setting up bandwidth limitations in Jellyfin's transcoding settings.

## Performance Optimization

For better performance:

1. **Transcoding Settings**:
   - In Dashboard → Playback, configure transcoding options
   - Enable hardware acceleration if your server supports it
   - Set an appropriate transcoding path (with fast storage)

2. **Library Scanning**:
   - Schedule library scans during off-peak hours
   - Disable "real-time monitoring" for large libraries

3. **Memory and CPU**:
   - Allocate sufficient resources based on your usage patterns
   - The default 2GB RAM / 2 CPU is good for medium-sized libraries

## Backup Strategy

Important data to back up:
- `/opt/data/jellyfin/config`: Contains all settings and user data

Your media files should be part of your regular backup strategy.

## Maintenance

### Viewing Logs

```bash
docker compose logs -f
```

### Database Maintenance

Occasionally, the Jellyfin database may need maintenance:
1. Stop Jellyfin: `docker compose stop`
2. Back up the config folder
3. Restart Jellyfin: `docker compose start`
4. Go to Dashboard → Advanced → Database and run "Scan for corruption"

## Links

- [Official Website](https://jellyfin.org/)
- [Documentation](https://jellyfin.org/docs/)
- [GitHub Repository](https://github.com/jellyfin/jellyfin)
- [Docker Hub](https://hub.docker.com/r/jellyfin/jellyfin)
- [Community Forum](https://forum.jellyfin.org/)
