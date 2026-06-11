# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A browser-based tic-tac-toe game with two game modes:
- **Single-player**: Play against an AI opponent with strategic behavior (tries to win, blocks your moves, plays smart)
- **Two-player**: Local multiplayer mode for playing against another person

The game is a single-file HTML application with embedded CSS and JavaScript. No build process or dependencies required.

## Project Structure

- `index.html` — Complete game in a single file
  - CSS (theming system with multiple color schemes via CSS variables)
  - JavaScript (game logic, AI, UI management)

## Running & Testing

**Open in browser**: Simply open `index.html` in any modern web browser. No server or build step needed.

**Testing the game**:
- Test single-player mode: click "Play vs AI", make moves, verify AI responds correctly
- Test two-player mode: click "Two Player", alternate players, verify win/draw detection
- Test game reset: click "New Game" and verify board clears
- Test mode switching: switch between modes mid-game and verify state resets

## Git Workflow

**Auto-commit/push is enabled**: After any code changes are committed, a post-commit hook automatically pushes to GitHub. No manual `git push` needed.

**Committing changes**:
1. When completing changes, run `git commit -m "message"`
2. The hook automatically runs `git push origin main`
3. All commits are attributed to `lvrdnck <leandro.verdonck@icloud.com>`

**Repository**: https://github.com/lvrdnck/tic-tac-toe

## Architecture Notes

The game uses a simple event-driven architecture:
- **Board state**: `board` array (9 elements, one per cell) stores 'X', 'O', or empty string
- **Game flow**: Click handler → move validation → state update → winner check → AI turn (if single-player) → display update
- **AI logic**: Prioritizes (1) winning move, (2) blocking opponent, (3) center control, (4) corners, (5) any available space
- **Win detection**: Checks against 8 predefined win conditions (3 rows, 3 columns, 2 diagonals)
- **Styling**: CSS variables (`--x`, `--o`, `--accent`, etc.) define all colors for easy theme switching

## Development Notes

- The HTML file may be auto-formatted/linted by the IDE; these changes are normal and should be committed
- Line ending warnings about CRLF are expected on Windows; no action needed
- Keep the game logic simple and contained within the single file for ease of deployment
