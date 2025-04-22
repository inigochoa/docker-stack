# HedgeDoc

## Overview

HedgeDoc (formerly CodiMD) is a real-time collaborative markdown editor. It
allows multiple users to edit the same document simultaneously, with live
preview. HedgeDoc is perfect for note-taking, documentation, technical
specifications, and more.

## Configuration

Copy the `.env.example` file to `.env` and adjust the values:

```bash
cp .env.example .env
```

| Variable | Description | Required |
|----------|-------------|----------|
| `CMD_DOMAIN` | Domain name | Yes |
| `CMD_SESSION_SECRET` | Secret for session encryption | Yes |
| `PGID` | User/Group IDs | Yes |
| `PUID` | User/Group IDs | Yes |
| `SERVICE_FOLDER_CONFIG` | Directory containing stack config | Yes |
| `SERVICE_FOLDER_DATA` | Directory containing stack data | Yes |
| `SERVICE_FOLDER_UPLOADS` | Directory containing stack uploads | Yes |
| `SERVICE_PORT` | Port for the web interface | Yes |
| `TZ` | Timezone | Yes |

## Important: Session Secret

To generate a secure session secret, run:
```bash
openssl rand -hex 32
```
Copy the output to the `CMD_SESSION_SECRET` variable in your `.env` file.

## Volumes

- `${SERVICE_FOLDER_CONFIG}:/config`: Configuration files
- `${SERVICE_FOLDER_DATA}:/hedgedoc/data`: SQLite database
- `${SERVICE_FOLDER_UPLOADS}`: Uploaded files and images

## Features

- Real-time collaborative editing
- Markdown with live preview
- Support for diagrams (Mermaid, FlowChart, etc.)
- Code syntax highlighting
- Math formula support (KaTeX)
- Slide presentation mode
- Document export (PDF, HTML, etc.)
- File uploads and image embedding

## Links

- [Official Website](https://hedgedoc.org/)
- [Documentation](https://docs.hedgedoc.org/)
- [GitHub Repository](https://github.com/hedgedoc/hedgedoc)
- [Docker Hub](https://hub.docker.com/r/linuxserver/hedgedoc/)
