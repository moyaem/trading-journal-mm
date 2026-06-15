# Futures Trading App

A self-contained, mobile-first trading journal for futures traders. The entire application lives in a single `index.html` file — no build step, no server, no dependencies to install. All data is stored locally in your browser via `localStorage`, and the app can be installed to your phone's home screen as a Progressive Web App (PWA).

**Live app:** https://moyaem.github.io/trading-journal-mm/

---

## Overview

This is a personal trading journal built for logging futures trades, tracking performance, managing prop firm accounts, and reflecting on trading psychology. It runs entirely in the browser with a dark, app-style interface designed for daily use on a phone.

Supported instruments out of the box: GC, MGC, NQ, MNQ, ES, MES, CL, and MCL (plus an "Other" option for anything else).

---

## Features

### Home

A dashboard landing screen showing:

- **This Week card** — total P&L for the current trading week (Sunday through Friday), trade count with wins/losses, and current market status.
- **Quick stats** — all-time win rate, total trades, and profit factor.
- **Weekly Insights** — automatically generated observations from your closed trades.
- **Recent Trades** — your last five entries at a glance.

### Trade Logging

Accessed via the central **+** button. Each trade captures a full picture:

- Instrument, date, entry/exit times, direction, contracts, and status
- Session, entry/exit price, and P&L (auto-calculated or manually overridden)
- Risk amount and actual R:R (auto-calculated)
- Playbook/strategy selection with a criteria checklist
- Execution quality, auto-graded F through A+ based on hard-rule and criteria compliance
- Account type, with prop firm account linking
- Pre-entry mindset (multi-select) and mindset during the trade
- Account balance before and after
- Free-form notes and screenshot uploads

### Journal

A sortable, filterable table of every trade:

- Filters arranged in a 2-column grid: date range, instrument, setup/strategy, account, direction, and status
- A **Custom Range** date option with from/to pickers
- Win/loss row highlighting toggle
- A **Read** button to view full notes for any trade
- Per-trade **Edit** and **Delete** actions
- One-tap **CSV export** of all trades

### Analytics

A deep dashboard with seven filters (direction, instrument, session, playbook/setup, mindset, account, and date range) that apply across every chart and metric on the page. Includes:

- Key performance metrics
- Cumulative P&L chart
- Win/loss breakdown
- Win rate by setup and by session
- P&L by setup and by day of week
- Rule compliance and mindset analytics
- A P&L calendar with clickable day-detail views

A **Clear Filters** button resets everything in one tap.

### Playbook (Strategies)

Define and manage your trading strategies. Each playbook entry has a name, description, an entry-criteria checklist, and hard rules. Playbooks are dynamically linked to the trade log — adding, editing, or deleting a strategy is immediately reflected in the trade form's setup dropdown, the journal filter, and analytics.

### Mindset

Log reflections on your trading psychology with structured prompts (what went well, what to improve, rule adherence). Each reflection can be edited or deleted.

### Prop Firms

Manage prop firm accounts with stage-aware behavior:

- **Evaluation** — shows a profit-target progress bar
- **Passed/Funded** — shows a buffer bar tracking profit past the drawdown threshold, plus a **Profit Withdrawals** section
- **Failed/Closed/Reset** — shows an "Account Closed" overlay

The withdrawal tracker records each withdrawal with a date, amount, profit split (80/20 or 90/10), and an auto-calculated take-home figure. Withdrawals can be edited or deleted.

---

## Installing as a Mobile App (PWA)

1. Open the live app URL in your phone's browser (Chrome on Android, Safari on iOS).
2. Open the browser menu and choose **Add to Home Screen**.
3. The app installs with its own icon and launches full-screen like a native app.

To update the installed icon after a new release, uninstall the existing app, reload the page, and reinstall.

---

## Data & Privacy

All data is stored locally on your device using the browser's `localStorage`. Nothing is sent to any server. The data lives under these keys:

- `tj_trades` — all logged trades
- `tj_strategies` — playbook entries
- `tj_reflections` — mindset reflections
- `tj_propfirms` — prop firm accounts and withdrawals

Because data is device-local, clearing your browser data or uninstalling the PWA will remove it. Use the **CSV export** in the Journal regularly to keep a backup.

---

## Technical Notes

- **Single file:** The whole app is one `index.html` with inline CSS and JavaScript.
- **Charts:** Rendered with Chart.js 4.4.1.
- **Offline:** A service worker enables offline use once loaded.
- **Trading week:** The futures week is defined as Sunday 6:00 PM ET through Friday 5:00 PM ET, with the market closed Saturday. The Home "This Week" card uses a calendar Sunday-to-Friday range.
- **CSV import/export:** Trades export to CSV and can be re-imported, with fingerprint-based deduplication to avoid duplicate entries.

---

## Deployment

The app is hosted on GitHub Pages. To deploy an update, replace `index.html` in the repository with the latest version and wait roughly a minute for GitHub Pages to refresh.
