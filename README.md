# Eastbound — daily routine tracker

A responsive, dependency-free website for a Tuesday–Saturday motorcycle commute from Binangonan, Rizal to Eastwood QC. Includes editable weekday schedules, dated completion checkmarks, weekly progress, and JSON backup import/export.

## Run locally

Requires Python 3 for the preview server; no packages or build tools needed.

```sh
python3 -m http.server 8000
```

Open http://localhost:8000. Keep using the same browser and address to retain your data. Stop the server with Ctrl+C.

## Your default workday

| Time | Activity |
| --- | --- |
| 4:00–4:30 AM | Wake, breakfast, gear |
| 4:30–6:00 AM | Motorcycle commute (budget 90 minutes) |
| 6:00–6:30 AM | Arrival buffer |
| 6:30 AM–3:30 PM | Shift, including a movable lunch break |
| 3:30–5:00 PM | Motorcycle commute home |
| 5:00–5:20 PM | Snack and decompress |
| 5:20–5:40 PM | Light exercise or mobility |
| 5:40–6:15 PM | Shower and dinner |
| 6:15–6:45 PM | Coding |
| 6:45–7:30 PM | Personal time |
| 7:30–8:00 PM | Prepare and wind down |
| 8:00 PM–4:00 AM next day | Eight hours of sleep |

Ride estimates are the user's usual 60–90 minutes, not live traffic predictions. Leave earlier if conditions need more time; shorten optional evening activities after delays. Sunday and Monday use flexible recovery templates. Adjust lunch to your employer's actual break schedule.

## Use and persistence

- The initial date uses Asia/Manila. Select any date or press Today.
- Edit schedule changes that weekday's recurring template across all weeks. Add/remove activities and change names and times. Overnight end times display `(+1d)`. No overlap validation is imposed, so review your edited times.
- Checkmarks belong to the selected calendar date. Sleep is credited to the date when bedtime begins.
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
