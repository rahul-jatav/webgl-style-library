# WebGL Style Library — deploy notes for Claude

## Canonical file
`/Users/rahul/Downloads/three-styles-deploy/index.html` — this is the **only** file to edit.

The following are symlinks pointing here, kept for backwards compatibility — do NOT edit them directly:
- `/Users/rahul/Downloads/three-styles.html` → `index.html`
- `/Users/rahul/Documents/CLaude code/three-styles.html` → (chain resolves to `index.html`)

## Local dev
Dev server is launched via the `abyssdither` config in `.claude/launch.json` — serves `/Users/rahul/Documents/CLaude code/` on port 5180.

URL: `http://localhost:5180/three-styles.html` (works via symlink chain).

If the server is down, restart with `mcp__Claude_Preview__preview_start` using name `abyssdither`.

## Live site
- URL: https://webgl-style-library.vercel.app/
- Repo: https://github.com/rahul-jatav/webgl-style-library (personal account `rahul-jatav`)
- Vercel project auto-deploys on every push to `main`. No manual deploy step.

## Shipping a change
After editing `index.html`:

```bash
git -C /Users/rahul/Downloads/three-styles-deploy add -A
git -C /Users/rahul/Downloads/three-styles-deploy commit -m "<concise message>"
git -C /Users/rahul/Downloads/three-styles-deploy push
```

Vercel picks up the push and updates the live URL within ~30 seconds.

## SSH note
This machine has two GitHub identities. The deploy folder's git remote uses the alias `github-personal` (configured in `~/.ssh/config`) which routes to `~/.ssh/id_ed25519_personal`. The default `github.com` host uses the work key (`Rahul-rekise`). Don't change the remote URL.

## Stack
- Single static HTML file. No build step.
- Three.js r160 via importmap (CDN — unpkg)
- Tweakpane v4 (CDN — esm.sh)
- Phosphor Icons v2.1.1 (CDN)
- Fonts: Orbitron + Rajdhani (Google Fonts)
- Local assets: `magnific_make-the-blue-planet-come_2936376201.mp4`, `favicon.svg`
