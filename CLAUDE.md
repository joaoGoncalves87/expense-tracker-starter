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

React 19 + Vite app with no routing or external state management. `transactions` is the only shared state, owned by `App.jsx` and passed down as props.

**Component tree:**
- `App.jsx` — holds the `transactions` array and `handleAdd` callback; composes the three child components.
- `Summary.jsx` — receives `transactions`, computes `totalIncome`, `totalExpenses`, and `balance` internally.
- `TransactionForm.jsx` — owns its own form state; calls `onAdd(transaction)` prop on submit. Converts `amount` to a number via `parseFloat` before passing up.
- `TransactionList.jsx` — receives `transactions`; owns its own `filterType` and `filterCategory` state.

**Transaction shape:** `{ id, description, amount, type, category, date }` — `amount` is a number, `type` is `"income"` or `"expense"`, `category` is one of `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.
