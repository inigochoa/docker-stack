# FreshRSS

## Overview

FreshRSS is a self-hosted RSS feed aggregator like the late Google Reader. It's
designed to be lightweight, easy to use, and flexible. Perfect for personal use
and following your favorite websites.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `CRON_MIN` | Feed update frequency (cron format) | Yes |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_FOLDER_EXTENSIONS` | Directory containing extensions data | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_DATA}:/var/www/FreshRSS/data`: Contains all your feeds,
  articles, and configurations
- `${SERVICE_FOLDER_EXTENSIONS}:/var/www/FreshRSS/extensions`: Custom extensions
  for FreshRSS

## Personal Usage Tips

For single-user scenarios:
- SQLite is sufficient and simpler than MySQL
- The default memory limits are generous for personal use
- Consider enabling the full-text search extension
- Use the mobile apps for reading on the go

## Feed Management

- Add feeds through the web interface
- Import OPML files from other readers
- Organize feeds with categories
- Use the bookmarklet to quickly subscribe to websites

## Extensions

FreshRSS supports extensions for added functionality:
1. Navigate to Extensions in the web interface
2. Enable built-in extensions like:
   - Share with Shaarli
   - Readability
   - Fix Article Content
   - OPML Import/Export

For custom extensions, place them in the `/opt/data/freshrss/extensions`
directory.

## Mobile Apps

Compatible with apps that support the Fever or Google Reader API:
- [FeedMe](https://play.google.com/store/apps/details?id=com.seazon.feedme) (Android)
- [Reeder](https://apps.apple.com/app/reeder-5/id1529445840) (iOS)
- [ReadYou](https://github.com/Ashinch/ReadYou) (Android)

## API Access

To enable API access for mobile apps:
1. Go to Settings > Authentication
2. Enable the API (Fever or Google Reader)
3. Set up your API password

## Links

- [Official Website](https://freshrss.org/)
- [Documentation](https://freshrss.github.io/FreshRSS/en/)
- [GitHub Repository](https://github.com/FreshRSS/FreshRSS)
- [Docker Hub](https://hub.docker.com/r/freshrss/freshrss/)
