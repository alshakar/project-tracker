# Project Follow-up Tracker

**Open the app:** [Project Follow-up Tracker](https://alshakar.github.io/project-tracker/)

The source entry point is [`index.html`](./index.html). It is a complete, self-contained web app with no build step or framework.

## Overview

Project Follow-up Tracker helps project managers monitor deliverables owned by other people. It brings overdue, due-soon, completed, and later work into one status-at-a-glance view and makes sending a follow-up possible in two taps: **Follow up**, then **Send**.

## Features

### Deliverables and projects
- Create, edit, and delete deliverables with a title, owner, optional email or phone contact, due date, project, and notes.
- Organize deliverables across multiple projects.
- Switch projects from the project menu.
- Create, rename, and delete projects.
- Deleting a project also removes its deliverables, with confirmation and a five-second Undo action.
- Delete individual deliverables with a five-second Undo action.
- Start from a project and load sample data when needed.
- Create a first project when no projects exist.

### Status and grouping
- Classifies deliverables as **Overdue**, **Due this week / Due soon**, **Done**, or **Later**.
- Calculates lateness in local calendar days.
- Sorts items by due date, with the most overdue items first.
- Groups cards under Overdue, Due this week, Later, and Done headings.
- Keeps the Done group collapsed by default.
- Uses text badges and status-specific colors, with an overdue card stripe.
- Shows tappable counters for Overdue, Due this week, and Done.
- Provides All, Overdue, Due soon, and Mine filters.
- The Mine filter uses the **Your name** setting.
- Shows clear empty states and filter-reset actions.

### Follow-up workflow
- Opens a follow-up sheet or dialog directly from each card.
- Preselects the appropriate tone:
  - **Gentle nudge** for items that are not overdue or are 1–2 days late.
  - **Reminder** for items 3–6 days late.
  - **Escalate** for items 7 or more days late.
- Provides Gentle nudge, Reminder, and Escalate chips.
- Generates a complete, editable follow-up message in the selected language.
- Sends through the Web Share API when available.
- Falls back to `mailto:` for email contacts and `sms:` for phone contacts.
- Disables Send when an item has no valid contact while keeping Copy available.
- Offers Copy with Clipboard API support and a manual-selection fallback.
- Asks **Did you send it?** after Send.
- Logs the follow-up date and tone only after a confirmed send.
- Displays the follow-up log in item detail.

### Item detail
- Tap a deliverable title to view its full details.
- Mark an item done or reopen it.
- Change the due date.
- Edit all deliverable fields.
- Delete the item.
- View a list of past sent follow-ups or the No follow-ups yet empty state.

### Settings
- Choose **System**, **Light**, or **Dark** theme.
- Choose **Match browser**, Arabic, or English language.
- Choose Western or Eastern Arabic digits.
- Set your name for the Mine filter.
- Reset to sample data with confirmation.
- Export all projects, deliverables, follow-up logs, and settings as JSON.
- Import a valid exported JSON file with confirmation.

### Storage and data recovery
- Saves data locally under `followup-tracker:v1` in `localStorage`.
- Keeps the app working in memory if browser storage is blocked or full.
- Shows a dismissible storage-off banner.
- Handles unreadable saved data by using sample data and offering Start fresh.
- Export and import make data portable and enable recovery or sharing.

### Languages and localization
- Opens in Arabic when the browser language starts with `ar`; otherwise it opens in English.
- Remembers explicit language changes.
- Updates `<html lang>` and `<html dir>` immediately.
- Uses logical CSS properties for left-to-right and right-to-left layouts.
- Formats dates and numbers with `Intl.DateTimeFormat` and `Intl.NumberFormat`.
- Uses Western or Eastern Arabic numbering when configured.
- Counts lateness in whole local calendar days.
- Uses `Intl.PluralRules` for day/days wording.
- Uses `<bdi>` and direction-aware rendering for mixed Arabic and English content.
- Keeps interface copy in an English and Arabic translation object.
- Bundles IBM Plex Sans and IBM Plex Sans Arabic as local WOFF2 assets for offline use.
- Includes Regular (400) and SemiBold (600) weights under [`fonts/`](./fonts/) and the SIL Open Font License in [`fonts/OFL.txt`](./fonts/OFL.txt).

### Responsive layout and accessibility
- Mobile-first layout designed around a 360px-wide phone.
- Two-column card layout at 600px and wider.
- Three-column card layout at 1024px and wider.
- Maximum content width of 1200px.
- Bottom sheets on phones and centered dialogs on larger screens.
- 56px floating Add button on phones and an Add deliverable button in the top bar on wider screens.
- Floating Add button moves to the bottom-left in Arabic.
- Light/dark themes use CSS variables.
- Light cards use the specified two-layer shadow; dark cards use divider borders without shadows.
- Tappable controls are at least 48px tall.
- Includes visible two-pixel focus rings.
- Supports keyboard Tab and Enter navigation.
- Supports Escape to close dialogs and sheets.
- Traps focus inside open dialogs.
- Uses live announcements for status, copy, import, undo, storage, and error messages.
- Respects `prefers-reduced-motion`.
- Respects safe-area insets.

### Sample data
- Loads relative-date sample projects and deliverables on first open.
- Includes the Website relaunch and Office move projects.
- Includes overdue, due-soon, later, and done examples.
- Includes an item with no contact to demonstrate the disabled Send state.
- Includes an existing follow-up log entry.
- Uses reserved `example.com` contact addresses.

## Running locally

This app has no build step. Serve the folder with any static server:

```bash
python3 -m http.server 4173
```

Then open <http://127.0.0.1:4173/index.html>.

## GitHub Pages

The app is deployed as a static site from [`index.html`](./index.html). With the repository configured to publish from the `main` branch and `/` (root), open:

<https://alshakar.github.io/project-tracker/>
