# Project: Offline Notes App

A simple note-taking mobile app built with React Native and Expo. All data is stored locally on the device — no cloud, no network, no authentication.

## Tech Stack

- **Runtime:** React Native with Expo SDK 52+
- **Language:** TypeScript (strict mode)
- **Routing:** expo-router (file-based)
- **Storage:** expo-sqlite for structured data, AsyncStorage for preferences
- **State:** React Context + useReducer (global), useState (local)

## Folder Structure

```
src/
  screens/        — Screen components (mapped by expo-router)
  components/     — Reusable UI components
  hooks/          — Custom React hooks
  utils/          — Pure helper functions
  storage/        — All database/storage access (single abstraction layer)
  types/          — Shared TypeScript types and interfaces
```

## Naming Conventions

- Components & types: `PascalCase` (`NoteCard.tsx`, `NoteType`)
- Functions & variables: `camelCase` (`formatDate`, `noteCount`)
- Files & folders: `kebab-case` (`note-card.tsx`, `use-notes.ts`)
- Constants: `UPPER_SNAKE_CASE` (`MAX_TITLE_LENGTH`)

## Hard Rules

- **No network calls.** Never add fetch, axios, analytics, auth, or any cloud service.
- **No inline styles.** Use `StyleSheet.create` exclusively.
- **No direct storage access in components.** Always go through `src/storage/` layer.
- **Prefer Expo-managed packages.** Only add third-party libs when Expo has no equivalent.
- **All code comments and commit messages in English.**

## Error Handling

- Wrap all storage operations in try/catch.
- Show user-friendly messages via toast/alert — never expose raw errors.
- Log errors with contextual info for debugging.

## Living Documents

- See [AGENTS.md](../AGENTS.md) for current project state, recent changes, and TODOs.
- See [mistakes.md](../mistakes.md) for known pitfalls and lessons learned.
