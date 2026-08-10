# AGENTS.md

## Project Overview

Android MDM (Mobile Device Management) system — a learning-oriented project with a 90-day roadmap. Currently at Day 0: no code yet, only the roadmap in `instruction.md`.

## Architecture Constraints

- **Server**: Next.js App Router + TypeScript + MongoDB + Socket.IO. Do NOT create a separate Express app.
- **Client**: Native Kotlin Android app. Do NOT use Expo/React Native — the project requires native Android Enterprise APIs.
- **Socket.IO**: Requires persistent server connections. Do NOT deploy to serverless-only platforms without explaining the limitation first.
- **Package boundaries**: `mdm-server/` (Next.js) and `mdm-client/` (Kotlin Android) are separate. Do not merge them.

## Security Rules

- Never bypass Android security, obtain root, or silently bypass user consent.
- Use Device Owner / Android Enterprise / DevicePolicyManager for device management.
- Use Device ID + token for authentication — never device ID alone.
- TLS in production, WSS for Socket.IO, never `CORS: "*"`.
- Never expose MongoDB credentials to Android APK or hardcode production secrets.

## Git Conventions

Conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `chore:`, `test:`. Commit at end of each session.

## Command Protocol

Every command sent to Android must produce a result. Commands flow: Dashboard → Next.js → Socket.IO → Android → Execute → Result → Next.js → MongoDB. Do not send raw video frames through Socket.IO (use WebRTC for screen streaming).

## Troubleshooting

When debugging, identify the failing layer first: Android UI → Android Service → Network → Socket.IO → Next.js → MongoDB. Fix one layer at a time.

## Development Workflow

Follow the daily task structure in `instruction.md` §7. Explain → Demonstrate → Code → Test → Commit → Review. Small working increments only.
