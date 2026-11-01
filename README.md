# Eastbound — daily routine tracker

A responsive, dependency-free website for a Tuesday–Saturday motorcycle commute from Binangonan, Rizal to Eastwood QC. Includes editable weekday schedules, dated completion checkmarks, weekly progress, and JSON backup import/export.

## Run locally

Requires Python 3 for the preview server; no packages or build tools needed.

```sh
python3 -m http.server 8000
```

Open http://localhost:8000. Keep using the same browser and address to retain your data. Stop the server with Ctrl+C.

## Night shift from November 7, 2026

Shift start dates are Tuesday–Saturday, 9:00 PM–6:00 AM the next morning. The first new shift is Saturday, November 7, ending Sunday, November 8 at 6:00 AM. November 6 and earlier keep the previous day-shift templates and checkmarks. Existing saved weekday edits remain available for that earlier period; a separate night template is initialized automatically, including when importing an older backup.

| Time | Activity |
| --- | --- |
| 4:00–4:30 PM | Wake and breakfast |
| 4:30–5:00 PM | Light exercise and shower |
| 5:00–6:00 PM | Coding |
| 6:00–6:30 PM | Main meal |
| 6:30–6:45 PM | Personal time |
| 6:45–7:00 PM | Pack food and riding gear |
| 7:00–8:30 PM | Ride to Eastwood (90-minute budget) |
| 8:30–9:00 PM | Arrival buffer |
| 9:00 PM–6:00 AM next day | Work, with adjustable midnight meal break |
| 6:00–7:30 AM next day | Ride home |
| 7:30–8:00 AM next day | Light meal, shower and wind down |
| 8:00 AM–4:00 PM next day | Eight hours of daytime sleep |

Begin the daytime sleep rhythm before the first shift if practical. Sunday and Monday nights are off, with editable recovery plans that keep the same sleep window. Saturday night's work ends Sunday morning. Travel budgets use your usual 60–90 minutes, not live traffic predictions. Adjust breaks to your actual workplace schedule.

## Use and persistence

- The initial date uses Asia/Manila. Select any date or press Today.
- Edit schedule changes that weekday's recurring template within the selected period (before November 7 or November 7 onward). Add/remove activities and change names and times. Rows are ordered: an earlier start time than the previous row moves to the next calendar day. Overnight rows and following morning rows show next-day labels. No overlap validation is imposed, so review your edited times.
- Checkmarks belong to the selected calendar date. All night-routine activities, including next-morning sleep, are credited to the selected shift start date.
- Weekly progress uses Monday–Sunday and counts Tuesday–Saturday activities, including future days. Recovery-day checkmarks are shown separately and excluded from the percentage.
- Existing activity IDs keep their checkmarks after edits. Removing an activity removes it from calculated totals, including historical totals; this is a personal tracker, not an immutable audit log.
- Data saves automatically in this browser's localStorage. There is **no account, server database, or automatic cross-device sync**. Clearing site data or changing browsers/website addresses will hide or remove it. Private browsing may discard it.
- Export backups regularly. Import validates a backup and asks before replacing current data. Storage errors are shown in the footer. Backups contain your schedule and habits; keep them private.
- Website edits do not modify GitHub source. Use GitHub commits to track code changes and backups to retain personal tracking data.

## Create the GitHub repository

Create an empty repository called `eastwood-routine` in your GitHub account, then run these commands from this folder (Git must be installed and authenticated):

```sh
git init -b main
git add index.html style.css app.js README.md .gitignore .github
git commit -m "Build Eastbound routine tracker"
git remote add origin https://github.com/YOUR_USERNAME/eastwood-routine.git
git push -u origin main
```

Alternatively, upload this folder's contents through GitHub, including `.github/workflows/pages.yml`.

## Deploy on GitHub Pages

1. In the repository, open **Settings → Pages**.
2. Choose **GitHub Actions** as the source.
3. Open **Actions → Deploy GitHub Pages → Run workflow** on `main` if the initial push occurred before Pages was enabled.
4. Wait for the workflow to succeed. The deployment URL appears in the workflow and Settings → Pages, usually `https://YOUR_USERNAME.github.io/eastwood-routine/`.

All asset links are relative, so project Pages paths work. The workflow publishes only the three website files. A public repository and public Pages site expose the default routine in source; personal checkmarks and browser edits are never sent to GitHub. Private repository Pages availability depends on the account plan, and site visibility must be checked separately.

## Modify the code

- `index.html`: page structure and copy
- `style.css`: responsive layout and colors
- `app.js`: schedule defaults, storage, editing, progress and backups
- `.github/workflows/pages.yml`: automatic deployment on pushes to `main`

Check syntax with `node --check app.js`. Preview in a browser and check a habit, reload, edit a weekday, switch dates, and export/import a backup before publishing changes.
