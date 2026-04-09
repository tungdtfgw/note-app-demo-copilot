---

name: 'React Native Standards'
description: 'Coding conventions for all TypeScript and React Native source files'
applyTo: 'src/**/*.tsx,src/**/*.ts'

---

# React Native Coding Standards

## Components

- Functional components only. Never use class components.
- Export components as named exports, one component per file.
- Keep components under 150 lines. Extract logic into custom hooks.
- Use `React.memo` only when you measure a performance issue — not by default.

## Styling

- Use `StyleSheet.create` at the bottom of each component file.
- No inline style objects, no CSS-in-JS libraries.
- Group styles logically: `container`, `header`, `content`, `footer`.
- Use consistent spacing values: 4, 8, 12, 16, 24, 32.

## Navigation

- Use expo-router file-based routing. Screen files live in `app/` directory.
- Use `<Link>` for declarative navigation, `router.push()` for imperative.
- Pass minimal params — prefer loading data from storage inside the target screen.

## State Management

- **Local state:** `useState` for UI-only state (modals, inputs, toggles).
- **Global state:** React Context + `useReducer` for shared app state (notes list, settings).
- Never put storage calls inside reducers. Dispatch actions, then persist in the hook/effect.

## Storage

- All database access goes through `src/storage/`. Components never import sqlite or AsyncStorage directly.
- Storage functions should be async, return typed results, and handle their own errors.
- Name storage functions clearly: `getNoteById`, `saveNote`, `deleteNote`, `searchNotes`.

## Lists

- Use `FlatList` for any list that could grow beyond ~20 items.
- Always provide `keyExtractor` returning a string.
- Implement `getItemLayout` when items have fixed height.

## Accessibility

- Add `accessibilityLabel` to all touchable elements and icons.
- Use `accessibilityRole` (button, header, link) where appropriate.
- Ensure touch targets are at least 44x44 points.

## Platform

- Use `Platform.select()` or `Platform.OS` checks when behavior differs.
- Avoid `.ios.tsx` / `.android.tsx` split files unless the implementations are fundamentally different.

## TypeScript

- Define shared types in `src/types/`. Co-locate component-specific types in the component file.
- Use `interface` for object shapes, `type` for unions and intersections.
- No `any`. Use `unknown` + type guards when the type is genuinely uncertain.
