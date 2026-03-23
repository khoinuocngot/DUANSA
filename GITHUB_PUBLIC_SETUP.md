# GitHub Public Upload Setup

This repo is now prepared so the real Firebase web config does not need to live in the public source code.

## What changed

- `D:/web/moinhatweb.html` now uses placeholders instead of real Firebase values.
- The comment widget falls back safely if comment secrets are not injected yet.
- The game leaderboard falls back to local mode if game secrets are not injected yet.
- `.github/workflows/deploy-pages.yml` injects the real Firebase values only inside the GitHub Pages build artifact.

## Add these GitHub Secrets

In GitHub: `Settings -> Secrets and variables -> Actions`

Comment Firebase:

- `GROUP2_COMMENT_FIREBASE_API_KEY`
- `GROUP2_COMMENT_FIREBASE_AUTH_DOMAIN`
- `GROUP2_COMMENT_FIREBASE_PROJECT_ID`
- `GROUP2_COMMENT_FIREBASE_STORAGE_BUCKET`
- `GROUP2_COMMENT_FIREBASE_MESSAGING_SENDER_ID`
- `GROUP2_COMMENT_FIREBASE_APP_ID`
- `GROUP2_COMMENT_FIREBASE_MEASUREMENT_ID`
- `GROUP2_COMMENT_FIREBASE_DATABASE_URL`

Game Firebase:

- `GROUP2_GAME_FIREBASE_API_KEY`
- `GROUP2_GAME_FIREBASE_AUTH_DOMAIN`
- `GROUP2_GAME_FIREBASE_PROJECT_ID`
- `GROUP2_GAME_FIREBASE_STORAGE_BUCKET`
- `GROUP2_GAME_FIREBASE_MESSAGING_SENDER_ID`
- `GROUP2_GAME_FIREBASE_APP_ID`
- `GROUP2_GAME_FIREBASE_MEASUREMENT_ID`
- `GROUP2_GAME_FIREBASE_DATABASE_URL`

Arcade Firebase:

- `GROUP2_ARCADE_FIREBASE_API_KEY`
- `GROUP2_ARCADE_FIREBASE_AUTH_DOMAIN`
- `GROUP2_ARCADE_FIREBASE_PROJECT_ID`
- `GROUP2_ARCADE_FIREBASE_STORAGE_BUCKET`
- `GROUP2_ARCADE_FIREBASE_MESSAGING_SENDER_ID`
- `GROUP2_ARCADE_FIREBASE_APP_ID`
- `GROUP2_ARCADE_FIREBASE_MEASUREMENT_ID`
- `GROUP2_ARCADE_FIREBASE_DATABASE_URL`

## Deploy

1. Push this repo to GitHub.
2. Add the secrets above.
3. Enable GitHub Pages for the repository.
4. Push to `main` or `master`, or run the `Deploy GitHub Pages` workflow manually.

## Important note

This keeps real Firebase values out of the repository and out of GitHub secret scanning for source files.

It does **not** make a client-side Firebase web config permanently secret after deployment, because the browser still needs that config at runtime. The safe part here is that the values are no longer stored in the public repo and commit history by default.

If real Firebase values were already committed or pushed before, clean the git history and rotate the affected Firebase credentials/project settings if needed.
