# Project Goal and Handoff

Last reviewed: 2026-10-25. Feature status is based on the current README and repository layout; verify live WhatsApp account behavior only with an authorized test account.

## Goal
Provide an MCP server that lets a configured agent search/read WhatsApp data and send user-authorized messages through a local bridge, while keeping message storage local in SQLite.

## Feature inventory

### Implemented / documented
- Go bridge connecting to a personal WhatsApp account through the WhatsApp multi-device API via `whatsmeow`.
- Search and read messages, including image, video, document, and audio attachments.
- Contact search; sending messages to individuals and groups.
- Sending media files such as images, videos, documents, and audio.
- Local SQLite storage for WhatsApp message data.
- MCP server configuration documented for Claude Desktop and Cursor.
- Optional FFmpeg support for converting audio to OGG/Opus voice messages; sending raw files does not require conversion.

### Partial / needs verification
- QR login, session persistence, reauthentication, attachment retrieval, and media sending need integration testing with an authorized account and the current WhatsApp/whatsmeow versions.
- Windows builds require CGO and a working C compiler, as documented in the README.
- Do not infer that every attachment type or large-message edge case works from the feature list alone.

### Not yet specified
- A separate roadmap of unimplemented features is not identified in the current root README. Add only confirmed missing requirements; do not invent a roadmap.

## Handoff notes for the next agent
1. Read the README and inspect the Go bridge plus Python MCP server before changing the protocol or storage.
2. Never log, commit, or expose WhatsApp credentials, session keys, QR payloads, message contents, or private database contents.
3. Treat message sending and media sending as side effects; preserve clear user authorization and error reporting.
4. Keep local SQLite storage and attachment handling consistent with the documented behavior.
5. Run Go/Python checks that exist in the current repository and exercise the MCP tool path after changes. Record actual outcomes here.

## Validation
The README contains setup instructions but this file does not claim a fresh login, message send, test, or build was performed today.
