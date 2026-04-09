# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install      # install dependencies (required before first run)
npm run dev      # start dev server at http://localhost:5173
npm run build    # production build
npm run lint     # run ESLint
npm run preview  # preview production build
```

## Architecture

This is a single-component React app (Vite + React 19). All state and logic lives in `src/App.jsx` — there are no child components, routing, or external state management.

**State in `App.jsx`:**
- `transactions` — array of `{ id, description, amount, type, category, date }`. `amount` is stored as a string (known bug).
- Form state: `description`, `amount`, `type`, `category`
- Filter state: `filterType`, `filterCategory`

**Known issues (intentional — this is a course starter project):**
- `amount` is stored as a string, so `totalIncome`/`totalExpenses`/`balance` calculations using `.reduce` produce incorrect results (string concatenation instead of numeric addition).
- UI styling is basic and intentionally rough.
