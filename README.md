# NightHacking archive (prototype)

A read-only static rebuild of **nighthacking.tv**, a site that ran on WordPress and was later compromised. Text and a small set of cleared images were exported from a forensic copy of the old site. The pages here are rebuilt from that export by a Python script. Nothing is copied from the old theme, plugins or database.

**Status: prototype, unreviewed.** A preview is published at https://steveonjava.github.io/nighthacking-tv-archive/ by `.github/workflows/pages.yml`, only after a pull request is merged to `main`. Every page carries `noindex,nofollow`. nighthacking.tv does not serve this build. The preview lives only at the github.io address above.

## What is in the prototype

Two recovered posts: JavaOne Interview with Gerrit Grunwald (2013-09-15) and Brian Goetz on Generic Specialization (2016-02-08). Every record is labelled `unreviewed`. The wording, dates and images are exactly what the export produced, so errors in the originals remain.

## What is deliberately not here

- Comments and user data
- Drafts, private and password-protected posts
- Executable code, plugins and theme code of the old site
- Original image files (the export re-encodes the pixels without metadata)
- Material from the old subdomains (the owner chose to ignore them)
- A transcript or copy of any video. Video posts link to YouTube.

## How it is built and checked

GitHub Actions only. `build.yml` has read-only permissions, no secrets, and pinned actions. `pages.yml` runs on merge to `main`, rebuilds with the project path prefix, and deploys with the minimum extra permissions (`pages: write`, `id-token: write`) in its deploy job only. It runs the unit tests, builds the site, audits links, drives a headless browser through the pages (including with JavaScript off) and uploads a 7-day preview artifact. See `docs/BUILD.md` for the input format.

## Records kept next to the content

- `recovery-manifest.json`: which posts and images the export contains, with hashes and what was excluded
- `rights.json`: one rights entry per image. Every entry is "owner-asserted, unreviewed" until a person clears it.
- `link-status.json` and `docs/link-checks.md`: the external link and video checks, with date and method
- `AGENTS.md`: the rules for any agent that works on this repository

Part of the work to rebuild Stephen Chin's public record around [stephenchin.com](https://stephenchin.com).
