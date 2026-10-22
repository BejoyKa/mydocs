# Daily Tech Dose

A newspaper-style page of the day's most important tech news, refreshed every morning by Claude.

- `index.html` is today's edition. GitHub Pages serves it at `https://<user>.github.io/<repo>/`.
- `archive/` keeps every past edition.
- `prompt/SKILL.md` holds the editorial rules Claude follows. Edit it to change scope or style.
- `scripts/template.html` is the page shell (masthead, CSS, footer).
- `.github/workflows/daily-refresh.yml` runs `scripts/generate.py` only when you ask: the **Fetch latest news** button on the page, or **Run workflow** on the Actions tab. There is no daily schedule, so the API is only used when you click.

## One-time setup

1. Push this folder to a new GitHub repository.
2. **Settings → Secrets and variables → Actions → New repository secret**: name it `ANTHROPIC_API_KEY` and paste your key from console.anthropic.com.
3. **Settings → Pages**: Source "Deploy from a branch", branch `main`, folder `/ (root)`.
4. **Actions** tab: open "Daily Tech Dose refresh" and click **Run workflow** to test it now.

## Fetch latest news button

The first time you click it, the page asks for a GitHub fine-grained token (repository `mydocs` only, permission **Actions: Read and write**). It is saved in that browser only, never in the repo. Visitors without a token can't trigger a refresh.

## Optional settings (Settings → Secrets and variables → Actions → Variables)

- `CLAUDE_MODEL`: defaults to `claude-opus-5-5`. Pick a smaller model to lower the cost.
- `MAX_SEARCHES`: defaults to 30 web searches per edition.

## Safety checks

The script refuses to publish an edition with fewer than 6 stories, no lead story, or a story missing its source link. When that happens, yesterday's page stays up and the failed run shows in the Actions tab.
