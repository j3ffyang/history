# AGENTS.md

## Project

Repository of historical and literary articles — Five Dynasties & Ten Kingdoms, silk, *Dream of the Red Chamber*, and Chinese classical literature. All articles are written in Chinese.

## Working rules

The universal working rules (approval before changes, commit only when asked, honesty, ground truth, rollback, brand conventions) are defined in the global `~/.config/opencode/AGENTS.md` and apply here too. This file adds only what is specific to this repo.

- **Verify facts before publishing.** Historical and literary claims need at least one independent, reliable source before publishing. A well-established primary-text fact needs only one verified primary-text source. Contested, interpretive, or attributive claims need at least two independent, reliable sources. Trusted sources include primary-text archives (e.g. Wikisource) and official academic institutions (e.g. kaogu.cn and cssn.cn). Academic presses (e.g. Zhonghua Book Company) and Wikipedia entries with references also count. Weibo, WeChat, Toutiao, Douyin/TikTok, and personal blogs do not count. Do not assert anything that cannot be verified. Put unverifiable or contradictory items in a batch corrections doc (`docs/YYMMDD-corrections-by-citation.md`) under "待核实". Create that doc only when there is something to record. See `docs/260808-corrections-by-citation.md` for the working example.
- **Quote the original.** Where the original text supports a claim, quote it verbatim in the article, with its chapter or source. Name the edition used. Where editions differ in wording, note the variant instead of silently choosing one.
- **Separate interpretation from fact.** Label allegorical, 索隐 (hidden-meaning), autobiographical, or family↔state readings as the *reader's interpretation*. Attribute each reading to a named school or scholar (e.g. 蔡元培's 索隐 school, 胡适's 考证/自传 school). Never state such a reading as the text's or author's explicit meaning. Where useful, cite the work's own boundary statements (e.g. 《红楼梦》第一回 "无朝代年纪可考" / "将真事隐去") as the limit. Verifiable textual facts (chapter numbers, quotations, dates) are still asserted as facts, with evidence.

## Filename conventions

Every file in `docs/` and `imgs/` follows a `YYMMDD-slug` pattern: a 6-digit date (`YYMMDD`, no `HHMM`, no `YYYY-MM-DD`), a hyphen, then a lowercase slug. No spaces.

- **Articles** — `docs/<YYMMDD>-<slug>.md`, e.g. `260604-five-dynasties-ten-kingdoms-article-zh-hans.md`.
- **Images** — `imgs/<YYMMDD>-<slug>.<ext>`; images for an article share the article's `YYMMDD` prefix.
- **Screenshots / captures with no meaningful name** — keep the capture time as the slug, e.g. `260604-074056.png`.
- **Renaming** — when a file is renamed, update every `../imgs/<file>` and doc link that referenced the old name.

## Repository layout

- `docs/` — article Markdown files and `YYMMDD-corrections-by-citation.md` (see "Filename conventions"). Unpublished drafts (writing skeletons, outlines, work-in-progress articles) may live here while they are untracked. Write a draft directly to its final filename; do not add a `-draft` suffix. Untracked status already marks a file as a draft. Commit only finished articles and corrections docs; never commit a draft or skeleton unless the user names it. Scratch files that are not drafts (temporary output, backups) do not belong in `docs/`.
- `imgs/` — article images (see "Filename conventions").
- `README.md` — index, edited by hand. Keep it in sync whenever articles are added, moved, or removed. **Only add a row for an article that is committed (or committed in the same change). Never add a row for an untracked, work-in-progress draft** — a row pointing to an uncommitted file renders a broken link.

## Conventions

- Articles reference images with a relative path (`../imgs/<file>`); keep `docs/` and `imgs/` as sibling directories so those links stay valid.
- Chinese articles use Simplified Chinese by default; Traditional Chinese only when the article was originally written that way. After drafting, scan for Traditional/variant characters that may have slipped in (e.g. 嬤/嬷, 與/与, 歸/归) and fix them.
- **Prose wrapping.** Prose auto-wraps; there is no hard-wrap requirement. Write each paragraph as a single line and let the renderer wrap it. Never split a CJK word across a line break. List items, code spans, and headings keep their own structure.
- **Quotation marks.** Use straight ASCII double quotes (`"`) for quotations in articles. Do not substitute full-width curly quotes (“ ”); reserve corner brackets (「 」) for corrections/校勘 documents.
- **Bold + quoted terms.** When a quoted term is also bolded, keep the quotes *outside* the emphasis markers — write `"**term**"`, not `**"term"**`. In CommonMark an opening `**` immediately followed by `"` is not left-flanking when preceded by a word character, so the asterisks render literally instead of bolding. The same rule applies to any delimiter adjacent to emphasis (quotes, `《》`, brackets): put them outside `**`.
- This directory is a separate git repository (a submodule of the parent `negtivSpace` repo) with two remotes on `main`: `j3ffyang` and `negtivspace` — push to both, then commit the updated submodule pointer in the parent.
