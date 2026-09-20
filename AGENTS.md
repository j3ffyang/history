# AGENTS.md

## Project

Bilingual (English · 中文) repository of historical and literary articles — Five Dynasties & Ten Kingdoms, silk, *Dream of the Red Chamber*, and Chinese classical literature. All articles are written in Chinese.

## Working rules

The universal working rules (approval before changes, commit only when asked, honesty, ground truth, rollback, brand conventions) are defined in the global `~/.config/opencode/AGENTS.md` and apply here too. This file adds only what is specific to this repo.

- **Verify facts before publishing.** Historical and literary claims in articles must be cross-checked against at least two independent, reliable sources before being treated as fact. Trusted sources: primary-text archives (e.g. Wikisource), official academic institutions (e.g. the Chinese Academy of Social Sciences' kaogu.cn and cssn.cn), academic presses (e.g. Zhonghua Book Company), and Wikipedia entries that carry references. Not counted: Weibo, WeChat, Toutiao, Douyin/TikTok, and personal blogs. Anything that cannot be verified is NOT asserted in the article. Unverifiable or contradictory items go into a batch corrections doc (`docs/YYMMDD-corrections-by-citation.md`) under "待核实" instead of being asserted in the article. The corrections doc is created only when there is something to record; if every claim verifies, no doc is needed. See `docs/260808-corrections-by-citation.md` for the working example.
- **Separate interpretation from fact.** Allegorical, 索隐 (hidden-meaning), autobiographical, or family↔state readings must be explicitly labelled as the *reader's interpretation* and attributed to a named school or scholar (e.g. 蔡元培's 索隐 school, 胡适's 考证/自传 school) — never stated as the text's or author's explicit meaning. Where useful, cite the work's own boundary statements (e.g. 《红楼梦》第一回 "无朝代年纪可考" / "将真事隐去") as the limit. Verifiable textual facts (chapter numbers, quotations, dates) are still asserted as facts, with evidence.

## Filename conventions

Every file in `docs/` and `imgs/` follows a `YYMMDD-slug` pattern: a 6-digit date (`YYMMDD`, no `HHMM`, no `YYYY-MM-DD`), a hyphen, then a lowercase slug. No spaces.

- **Articles** — `docs/<YYMMDD>-<slug>.md`, e.g. `260604-five-dynasties-ten-kingdoms-article.md`.
- **Images** — `imgs/<YYMMDD>-<slug>.<ext>`; images for an article share the article's `YYMMDD` prefix.
- **Screenshots / captures with no meaningful name** — keep the capture time as the slug, e.g. `260604-074056.png`.
- **Renaming** — when a file is renamed, update every `../imgs/<file>` and doc link that referenced the old name.

## Repository layout

- `docs/` — article Markdown files (see "Filename conventions").
- `imgs/` — article images (see "Filename conventions").
- `README.md` — bilingual index, edited by hand. Keep it in sync whenever articles are added, moved, or removed.

## Conventions

- Articles reference images with a relative path (`../imgs/<file>`); keep `docs/` and `imgs/` as sibling directories so those links stay valid.
- Chinese articles use Simplified Chinese by default; Traditional Chinese only when the article was originally written that way.
- **Prose wrapping.** Prose auto-wraps; there is no hard-wrap requirement. Write each paragraph as a single line and let the renderer wrap it. Never split a CJK word across a line break. List items, code spans, and headings keep their own structure.
- **Quotation marks.** Use straight ASCII double quotes (`"`) for quotations in articles. Do not substitute full-width curly quotes (“ ”); reserve corner brackets (「 」) for corrections/校勘 documents.
- This directory is a separate git repository (a submodule of the parent `negtivSpace` repo) with two remotes on `main`: `j3ffyang` and `negtivspace` — push to both, then commit the updated submodule pointer in the parent.
