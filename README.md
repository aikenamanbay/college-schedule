# College Schedule

A mobile-first college timetable prototype with a daily agenda, weekly calendar, configurable reminders, profile preferences and light/dark themes. Built with plain HTML, CSS and JavaScript.

## Run

Open **index.html** in a browser. No installation, build step or server is required. Keep `app.js`, `styles.css` and `assets/` beside the HTML file.

Optional local server:

```sh
python3 -m http.server 8080
```

Then open http://localhost:8080. Data is saved per browser origin, so a local server and a file URL use separate settings.

Use `?demo=1` to preview a fixed Monday, 19 October 2026 at 08:55 (UTC+5). Without it, the app uses the current date and time in Asia/Atyrau.

## Features

- **Today:** current or next lesson, progress and lesson status.
- **Week:** select a day or navigate between weeks; weekends have empty states.
- **Details:** lesson time, room, teacher, group and topic.
- **Reminders:** save a lesson with a 5, 10 or 15 minute lead; edit, open or remove saved reminders.
- **Profile:** edit name and group, save or cancel, choose the theme and default reminder interval.
- **Persistence:** profile, appearance and reminders are saved in localStorage.
- **Alerts:** a reminder banner and toast appear while the app remains open.

## Demo limitations

This is a local prototype, not a production student information system. Login does not authenticate an account. Reminder alerts work inside the open page; there are no background or system push notifications. The Monday timetable is based on the assignment; the remaining weekdays are illustrative. Demo profile details can be changed locally.

## Design

The primary palette follows the technical brief: `#4F46E5`, `#3730A3`, `#F5F7FB`, `#FFFFFF`, `#111827`, `#6B7280`, `#DC2626`, `#16A34A`. Dark mode uses the brief's bonus palette. The bundled typeface is Inter; its font licence is in `assets/Inter-OFL.txt`.

[Figma design](https://www.figma.com/design/iMMpr6q4hjJrzD9N2GZHaT?node-id=27-360) — six screens in two themes, imported as editable SVG artwork. The SVG copies are visual designs; working interactions are implemented in this repository. Source artwork is included in `figma/svg/`.

## Files

```text
index.html          App entry point
app.js              Views, state, timetable and interactions
styles.css          UI styles, tokens and themes
button.css          Standalone button CSS for assignment handoff
assets/             Local Inter font, licence and supplied logo
figma/svg/          Editable visual exports of all screens
scripts/            Browser checks and export scripts
```

## Verify

Node.js 20+ is required only for development tools.

```sh
npm ci
npx playwright install chromium
npm test
```

The browser scenario covers week/day navigation, weekends, statuses, reminder creation/editing/removal/persistence, past-class handling, profile save/cancel/defaults, theme persistence and logout.

To use an existing Chrome installation instead of bundled Chromium, set `CHROME_PATH` to its executable.

```sh
npm run screenshots
npm run export:svg
```

Generated screenshots are written to `png/`; fresh SVG exports are written to `svg/`.
