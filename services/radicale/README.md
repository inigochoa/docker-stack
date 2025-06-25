# Radicale

Radicale is a small but powerful CalDAV (calendars, to-do lists) and CardDAV
(contacts) server.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_DATA}:/var/www/radicale/data`: Radicale data

## Personal Usage Tips

For single-user scenarios:
- The default memory limits are generous for personal use

## Links

- [Official Website](https://github.com/tomsquest/docker-radicale)
