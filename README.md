# Offline Notes App

A simple, private note-taking app built with React Native + Expo. All data stays on your device.

## Getting Started

```bash
npx create-expo-app@latest offline-notes --template blank-typescript
cd offline-notes
npx expo install expo-router expo-sqlite @react-native-async-storage/async-storage
npx expo start
```

## Project Structure (See AGENTS.md)

## How Custom Instructions & Prompts Work

This project uses three layers of AI customization, designed to show how rules and prompts apply during real development.

### Layer 1: Fixed Rules (`copilot-instructions.md`)

These rules are **permanent** and loaded on every Copilot chat request. They define:

- Tech stack (Expo, TypeScript, expo-sqlite)
- Naming conventions (PascalCase components, camelCase functions, kebab-case files)
- Hard rules (no network calls, no inline styles, storage abstraction only)

You write these once and never touch them again.

### Layer 2: Targeted Rules (`react-native.instructions.md`)

These rules are **conditionally applied** only when you're editing files matching `src/**/*.tsx` or `src/**/*.ts`. They cover React Native specifics: functional components, StyleSheet.create, FlatList usage, accessibility, etc.

### Layer 3: Living Documents (`AGENTS.md` + `mistakes.md`)

These are **updated continuously** via prompt commands:

- `AGENTS.md` — Where the project is right now, what changed recently, what's next
- `mistakes.md` — What went wrong and how to avoid it

The agent reads both on every request, so it always has fresh context without you repeating yourself.

## Development Workflow

### Starting a feature

```
/git-branch → "add search to home screen"
            → creates feat/add-search-to-home-screen
```

### During development

| What you do           | What the agent enforces                                                   |
| --------------------- | ------------------------------------------------------------------------- |
| Create `NoteCard.tsx` | Functional component, StyleSheet.create, accessibilityLabel, named export |
| Add note storage      | Code in `src/storage/`, async functions, try/catch, typed returns         |
| Build the note list   | FlatList with keyExtractor, no inline styles                              |
| Try to use `fetch()`  | Blocked — "No network calls" rule                                         |

### Committing & pushing

```
/git-commit → reads staged diff
            → proposes: feat(storage): add note CRUD operations
            → you confirm → committed

/git-push   → shows 3 unpushed commits
            → you confirm → pushed
```

### When something goes wrong

```
/learn-from-mistake → "agent used inline style in NoteCard"
```

Agent adds to `mistakes.md`:

| Date       | Mistake                      | Root Cause                    | Fix / Rule                                           |
| ---------- | ---------------------------- | ----------------------------- | ---------------------------------------------------- |
| 2025-07-15 | Inline style in NoteCard.tsx | Agent ignored StyleSheet rule | Always use StyleSheet.create, no `style={{}}` in JSX |

### End of session

```
/wrap-up → agent reviews git log + conversation
         → updates AGENTS.md with current state, changes, TODOs
```

### The Feedback Loop

```
Code → Mistake → /learn-from-mistake → mistakes.md updated
                                              ↓
                              Agent reads it next session
                                              ↓
                                   Avoids same mistake

Session ends → /wrap-up → AGENTS.md updated
                                ↓
                  Agent knows where project left off
```

The key design: **`copilot-instructions.md` is the law** (stable), while **`AGENTS.md` and `mistakes.md` are the memory** (evolving). Together they give the agent both consistent rules and fresh context.
