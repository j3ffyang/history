# AGENTS.md

## Project

Bilingual (English · 中文) repository of historical and literary articles —
Five Dynasties & Ten Kingdoms, silk, *Dream of the Red Chamber*, and Chinese
classical literature. All articles are written in Chinese.

## Working rules

- **Get approval before any change.** Present the plan and wait for the
  user's explicit go-ahead before editing files, generating output, or
  running state-changing commands. If anything is unclear, ask rather than
  assume.
- **Commit only when asked.** Never commit, amend, or push unless the user
  explicitly requests it. When committing, stage only intended files.

## Filename conventions

Every file in `docs/` and `imgs/` follows a `YYMMDD-slug` pattern: a 6-digit
date (`YYMMDD`, no `HHMM`, no `YYYY-MM-DD`), a hyphen, then a lowercase slug.
No spaces.

- **Articles** — `docs/<YYMMDD>-<slug>.md`, e.g.
  `260604-five-dynasties-ten-kingdoms-article.md`.
- **Images** — `imgs/<YYMMDD>-<slug>.<ext>`; images for an article share the
  article's `YYMMDD` prefix.
- **Screenshots / captures with no meaningful name** — keep the capture time
  as the slug, e.g. `260604-074056.png`.
- **Renaming** — when a file is renamed, update every `../imgs/<file>` and doc
  link that referenced the old name.

## Repository layout

- `docs/` — article Markdown files (see "Filename conventions").
- `imgs/` — article images (see "Filename conventions").
- `README.md` — bilingual index, edited by hand. Keep it in sync whenever
  articles are added, moved, or removed.

## Conventions

- Articles reference images with a relative path (`../imgs/<file>`); keep
  `docs/` and `imgs/` as sibling directories so those links stay valid.
- Chinese articles use Simplified Chinese by default; Traditional Chinese
  only when the article was originally written that way.
- This directory is part of the parent `negtivSpace` repo (no separate git
  history). Do not create a nested `.git` here.
