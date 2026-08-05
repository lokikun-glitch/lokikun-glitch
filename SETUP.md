# Setup Instructions

This repo becomes your GitHub profile page once it lives at a repository
named **exactly** your GitHub username (e.g. `github.com/octocat/octocat`)
and is set to **public**.

## 1. Create the profile repository

1. On GitHub, create a new **public** repository named exactly your
   username (e.g. `lokikun-glitch/lokikun-glitch`).
2. GitHub will prompt "This is a special repository" — accept it.
3. Push the contents of this folder to that repository:

   ```bash
   git init
   git remote add origin https://github.com/lokikun-glitch/lokikun-glitch.git
   git add .
   git commit -m "Add profile README"
   git branch -M main
   git push -u origin main
   ```

## 2. Replace placeholders

Three placeholders appear throughout `README.md` and
`.github/workflows/snake.yml`. Replace every occurrence:

| Placeholder | Replace with | Files |
|---|---|---|
| `lokikun-glitch` | Your GitHub username | `README.md`, `.github/workflows/snake.yml` |
| `https://www.linkedin.com/in/lokesh-parate-1a41b1272/` | Full LinkedIn profile URL (e.g. `https://linkedin.com/in/yourname`) | `README.md` |
| `lokeshparate6@gmail.com` | Your contact email | `README.md` |

Fastest way — find/replace across the repo:

```bash
# macOS/Linux
grep -rl "lokikun-glitch" . | xargs sed -i '' 's/lokikun-glitch/<your-username>/g'

# Windows PowerShell
Get-ChildItem -Recurse -File | ForEach-Object {
  (Get-Content $_.FullName -Raw) -replace 'lokikun-glitch', '<your-username>' |
    Set-Content $_.FullName
}
```

Then repeat for `https://www.linkedin.com/in/lokesh-parate-1a41b1272/` and `lokeshparate6@gmail.com`.

## 3. Enable the contribution snake animation

The workflow at `.github/workflows/snake.yml` generates the animated
snake SVG and publishes it to an `output` branch automatically.

1. Confirm `github_user_name: lokikun-glitch` in
   `.github/workflows/snake.yml` has been replaced with your username.
2. Push to `main` — the workflow runs automatically (also runs daily
   at 00:00 UTC via cron, and can be triggered manually from the
   **Actions** tab using "Run workflow").
3. In your repo **Settings → Actions → General → Workflow permissions**,
   ensure **"Read and write permissions"** is selected so the workflow
   can push to the `output` branch.
4. After the first successful run, an `output` branch will exist
   containing `github-contribution-grid-snake.svg` and
   `github-contribution-grid-snake-dark.svg`. The README already
   references these via raw GitHub URLs — no further changes needed.

## 4. Verify the widgets

All stats widgets (`github-readme-stats`, `github-readme-streak-stats`,
`github-profile-trophy`, `github-readme-activity-graph`,
`github-profile-summary-cards`) read your public GitHub activity
automatically once `lokikun-glitch` is replaced — no API keys or
extra configuration required.

> **Note:** these are community-hosted widgets. If any image looks slow
> to load or briefly unavailable, that's normal (shared free hosting) —
> it will resolve on refresh and requires no action on your part.

## 5. Customize further (optional)

- **Theme:** All widgets currently use the `tokyonight` / `tokyo-night`
  theme for a consistent dark aesthetic. Swap the `theme=` query
  parameter on any widget URL to change it.
- **Projects:** Edit the *Featured Projects* section in `README.md` —
  update descriptions, tech badges, and repository links (currently
  placeholder slugs like `whatsapp-ai-notification-router`).
- **Assets:** `assets/hero-banner.svg`, `assets/divider.svg`, and
  `assets/footer-wave.svg` are plain SVG/XML — open and tweak colors,
  text, or sizing directly.
