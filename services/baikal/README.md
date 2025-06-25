# Baïkal

Baïkal is a lightweight CalDAV+CardDAV server. It offers an extensive web
interface with easy management of users, address books and calendars. It is fast
and simple to install and only needs a basic php capable server. The data can be
stored in a MySQL or a SQLite database.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `SERVICE_FOLDER_CONFIG` | Directory containing config data | Yes |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_CONFIG}:/var/www/baikal/config`: Baïkal configuration files
- `${SERVICE_FOLDER_DATA}:/var/www/baikal/Specific`: Baïkal data

## Personal Usage Tips

For single-user scenarios:
- SQLite is sufficient and simpler than MySQL
- The default memory limits are generous for personal use

## Links

- [Official Website](https://sabre.io/baikal/)
