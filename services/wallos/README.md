# Wallos

## Overview

Wallos is a subscription management tool that helps you track and manage your
recurring payments. It provides insights into your spending, sends notifications
for upcoming renewals, and helps you keep track of all your subscriptions in one
place.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_FOLDER_LOGOS` | Directory containing logos | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | `Europe/Madrid` | Yes |

## Volumes

- `${SERVICE_FOLDER_DATA}:/var/www/html/db`: Wallos application data
- `${SERVICE_FOLDER_LOGOS}:/var/www/html/images/uploads/logos`: Wallos logos

## Features

- Track all your subscriptions in one place
- Get reminders for upcoming renewals
- Analyze spending patterns over time
- Support for multiple currencies
- Categories and tags for organization
- Payment method tracking

## Links

- [Wallos GitHub Repository](https://github.com/ellite/Wallos)
- [Docker Hub](https://hub.docker.com/r/bellamy/wallos)
