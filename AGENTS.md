## Project Overview

Offline note-taking app — React Native, Expo, TypeScript, local storage only.

## Project Structure

project-root/
├── PRD.md                                 ← Product requirements
├── AGENTS.md                              ← Living doc: current state & recent changes
├── mistakes.md                            ← Living doc: lessons learned
├── app/                                   ← expo-router screens
│   ├── index.tsx                           ← Home (note list + search)
│   └── note/[id].tsx                       ← Editor (create / edit)
├── src/
│   ├── components/                        ← Reusable UI components
│   ├── hooks/                             ← Custom React hooks
│   ├── storage/                           ← All DB access (single layer)
│   ├── utils/                             ← Pure helper functions
│   └── types/                             ← Shared TypeScript types
├── .github/
│   ├── copilot-instructions.md            ← Fixed rules (never changes)
│   ├── instructions/
│   │   └── react-native.instructions.md   ← Auto-applied to src/**/*.ts(x)
│   └── prompts/
│       ├── git-commit.prompt.md           ← /git-commit
│       ├── git-push.prompt.md             ← /git-push
│       ├── git-pull.prompt.md             ← /git-pull
│       ├── git-branch.prompt.md           ← /git-branch
│       ├── git-worktree.prompt.md         ← /git-worktree
│       ├── git-merge.prompt.md            ← /git-merge
│       ├── wrap-up.prompt.md              ← /wrap-up
│       └── learn-from-mistake.prompt.md   ← /learn-from-mistake

## Data Model

```
Note {
  id: string (UUID)
  title: string
  body: string
  createdAt: number (timestamp)
  updatedAt: number (timestamp)
}
```

Storage: `expo-sqlite` — single `notes` table. All access through `src/storage/` layer.

## Screens

| Screen | Route        | Description                  |
| ------ | ------------ | ---------------------------- |
| Home   | `/`          | Note list + search bar + FAB |
| Editor | `/note/[id]` | Create or edit a note        |

Navigation: expo-router file-based routing. Minimum: iOS 15+, Android 10+.

## Current State

- **Phase:** Initial setup
- **Status:** Project scaffolded, no features implemented yet

## Architecture Decisions

- **expo-sqlite***
- **Storage abstraction layer (`src/storage/`)** 
- **Context + useReducer***
- **expo-router***
- **Auto-save with debounce***
- **No trash/archive for v1**

## TODOs

- [ ] Initialize Expo project with TypeScript template
- [ ] Set up expo-router file-based navigation
- [ ] Create storage abstraction layer (expo-sqlite)
- [ ] Build basic note CRUD screens
- [ ] Add search/filter functionality
