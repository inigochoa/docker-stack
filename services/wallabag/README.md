# Wallabag

## Overview

Wallabag is a self-hosted application for saving web pages. Unlike cloud-based
services, it guarantees you'll never lose your saved articles. With Wallabag,
you can save, read, tag, and search articles from anywhere.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_FOLDER_IMAGES` | Directory containing images | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `SYMFONY__ENV__DOMAIN_NAME` | Public domain name | Yes |
| `TZ` | Timezone | Yes |

## Volumes

- `${SERVICE_FOLDER_DATA}:/var/www/wallabag/data`: Application data
- `${SERVICE_FOLDER_IMAGES}:/var/www/wallabag/web/assets/images`: Saved images
  from articles

## Features

- Save articles from any device with browser extensions and mobile apps
- Read articles in a clean, distraction-free interface
- Tag and organize your readings
- Full-text search through all saved articles
- Export articles to PDF, EPUB, MOBI, etc.
- Highlight and annotate text
- Share articles with others

## Browser Extensions

- [Firefox](https://addons.mozilla.org/firefox/addon/wallabagger/)
- [Chrome](https://chrome.google.com/webstore/detail/wallabagger/gbmgphmejlcoihgedabhgjdkcahacjlj)

## Mobile Apps

- [Android](https://play.google.com/store/apps/details?id=fr.gaulupeau.apps.InThePoche)
- [iOS](https://apps.apple.com/app/id1170800946)

## Links

- [Official Website](https://www.wallabag.org/)
- [Documentation](https://doc.wallabag.org/)
- [GitHub Repository](https://github.com/wallabag/wallabag)
- [Docker Hub](https://hub.docker.com/r/wallabag/wallabag/)
