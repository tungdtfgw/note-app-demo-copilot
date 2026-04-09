# PRD: Offline Notes App

## Overview

A minimal note-taking app that runs entirely on-device. No accounts, no sync, no cloud — just open and write.

## Target Users

Anyone who wants a fast, private, no-frills note-taking app on their phone.

## Core Features

### 1. Note List (Home Screen)

- Display all notes as a scrollable list, sorted by last modified (newest first).
- Each item shows: title (or first line if no title), preview of body text, last modified date.
- Empty state: friendly message + button to create first note.

### 2. Create / Edit Note

- Tap "+" to create a new note, tap any note to edit.
- Fields: title (optional, single line), body (multiline, plain text).
- Auto-save on every pause (debounce 1 second) — no manual save button.
- Show "last saved" timestamp at the bottom.

### 3. Delete Note

- Swipe left on a note in the list to reveal delete button.
- Confirm with a simple alert: "Delete this note?" → Cancel / Delete.
- Deletion is permanent (no trash/archive for v1).

### 4. Search

- Search bar at the top of the home screen.
- Filters notes by title and body content (case-insensitive substring match).
- Results update as the user types (debounced 300ms).

## Non-Features (Explicitly Out of Scope)

- No folders, tags, or categories
- No rich text, markdown, or attachments
- No cloud sync, backup, or sharing
- No user accounts or authentication
- No dark/light theme toggle (follow system theme)
