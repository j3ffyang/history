---
name: character-name-literary-origins
description: >
  Trace character names in classical Chinese literature back to their poetic,
  allusive, or homophonic origins. Use when the user wants to analyze how an
  author named characters — e.g. 红楼梦丫鬟 names from《诗经》, 唐宋诗词;
  三国演义 names from《周易》; 金瓶梅 homophones; or any 文学人名考释 task.
  Covers creation, polishing, fact-checking, and citation of name-source articles.
  Output is in Simplified Chinese; source material may be in any language.
license: MIT
compatibility: opencode
metadata:
  author: j3ffyang
  version: 1.0.0
---

# Character Name Literary Origins (人名渊源考释)

Trace how authors name their characters — from classical poetry, allusions, homophones, cultural symbols, or fate-foreshadowing. The user supplies the character list and rough sources; you supply the structured research, verbatim citations, and polished analysis. Output is in Simplified Chinese; source material may be in any language.

This skill complements `chinese-history-literature-culture` (general Chinese literature articles). Use `character-name-literary-origins` when the article's core structure is **name → source → analysis** repeated for multiple characters. Use the general skill for other article types.

## Golden rules

1. **Follow the user's character list and ordering — must.** The user decides which characters to include and in what sequence. Never silently reorder, drop characters, or add characters the user did not request.
2. **Three mandatory elements per entry.** Every character entry MUST contain: (a) 个人背景 one-liner, (b) 诗词链接 verbatim quote, (c) 诗词赏析 analysis. No entry is complete without all three.
3. **Cite, don't assert.** Every source attribution gets checked against the primary text. Quoted lines must match the cited edition verbatim. Anything unverifiable goes into the corrections doc, not the article.
4. **Flag before replacing.** If the user's source attribution is wrong, keep their intent, propose the correction, and get approval before swapping (AGENTS.md: "Get approval before any change").
5. **Never cite a source you have not opened.** Every citation must be verified against the source's actual content — see Phase 3.
6. **Deduplicate ruthlessly.** Each fact appears once per entry. Biographical context does not repeat in the analysis. The 结语 covers all entries, not a subset.

## Inputs

- `source` — the user's raw text: a list of characters with rough source attributions, notes, or a stream of thought. May be pasted directly or given as a file path.
- `mode` — what the user wants this run:
  - `create` — turn a character list + rough notes into a full name-source article.
  - `polish` — improve an existing draft (grammar, flow, clarity, style) while preserving structure and voice.
  - `cite` — add/verify citations for an existing article (may combine with polish).
  - Default: follow whatever the user asked; ask if unclear.
- `author_work` — the literary work being analyzed (e.g.《红楼梦》《三国演义》《金瓶梅》).
- `audience` / `tone` — optional. Default: general literate audience interested in classical Chinese literature.

## Source quality — trusted vs. untrusted

**Trusted** (meet the ≥2-sources rule):
- Primary-text archives: Wikisource (维基文库) — classical texts, 诗文集, 小说原文.
- Official academic institutions: 中国社科院, 故宫博物院, 国家图书馆, university presses.
- Academic presses & canonical editions: 中华书局, 上海古籍出版社, 人民文学出版社, 商务印书馆.
- Wikipedia entries (维基百科) that carry references.
- Critical editions: 脂砚斋重评石头记 (甲戌本、庚辰本等), 毛诗正义, 全唐诗, 全宋词.

**NOT trusted**: 微博 / WeChat / 头条 / 抖音 / 个人博客 / 百度百科 无参考文献词条 / AI chat outputs.

## Workflow

### Phase 1 — Understand the character list (do not skip)

1. Read the user's input end to end.
2. Extract the **character list** and their rough source attributions.
3. For each character, note: name, source text (if known), any special features (谐音, 成对, 犯讳, etc.).
4. Restate the user's structure back to them: character order, grouping logic (if any), and source attributions.
5. Confirm with the user before writing, unless the list is unambiguous.

### Phase 2 — Research & source curation

For each character's name-source attribution:

6. **Search the web** for the name's origin. Prefer site-restricted queries against trusted domains: `site:zh.wikisource.org 诗经 月出`, `site:ctext.org 蜀道难`.
7. **Cross-check with at least two independent sources** for contested attributions. When sources disagree, record the discrepancy in the corrections doc.
8. **Prefer primary text over commentary.** Quote from the primary text (Wikisource, 中华书局点校本) and verify exact wording and chapter/回目 number.
9. **Verify chapter/回目 attributions against the original text**, not memory: e.g. for《红楼梦》check 回目 against the novel; for《诗经》check poem titles against《毛诗正义》.
9a. **Know when one source suffices.** Well-established facts (a poem's exact wording in Wikisource, a chapter number) need only one verified source. Reserve ≥2 sources for contested claims and interpretive assertions.

### Phase 3 — Source verification (verify the truth)

10. **Open each source and locate the exact passage.** Fetch the page and confirm the specific sentence appears there verbatim or in substance. If you cannot retrieve the full content, you may not cite it — put it in 待核实.
11. **Match claim ↔ source one-to-one.** Pair every fact with the exact sentence(s) that support it. If a source does not actually say what the draft claims, drop that source or fix the claim.
12. **Check source independence.** Two sources that copy one another count as ONE source. Look for genuinely independent origins — a primary text, an academic paper, an official institution.
13. **Watch for ghost citations.** A citation is suspicious if: the title looks plausible but no copy exists; the quoted sentence cannot be found; or search returns only secondary mentions. AI-generated and memory-invented citations must be detected and removed.

### Phase 4 — Write / polish

14. Write in Simplified Chinese by default. Follow the user's character order and emphasis.
15. **Each entry MUST contain three elements:**

```
## N、[名字]——[来源概括]

[个人背景 one-liner: who they serve, age, key traits]

[诗词链接: source text name + verbatim quoted line]

[诗词赏析: how the author adapted it, what it implies about the character's fate]
```

16. **Optional elements** (include when present):
    - 脂砚斋 or other commentator 批语 (bolded as `**脂砚斋**`, verbatim)
    - 谐音寓意 analysis (本名 → 谐音 meaning)
    - 命运暗示 connections (how name foreshadows fate)
    - 成对/成组 relationships (e.g. 琴棋书画, 金玉对仗)

17. **Remove duplication.** Each fact appears once per entry. After writing a section, cut any sentence that restates information already present — whether in the background one-liner, the analysis, the introduction, or the conclusion. Common patterns:
    - Biographical context repeating in the analysis paragraph
    - 结语 echoing the introduction
    - Two paragraphs in the same entry making the same point

18. **Group related entries** when multiple characters share the same source or naming pattern (e.g. all 诗经 sources, all 琴棋书画 names). Use a shared section header, then sub-entries.

19. Use precise terminology with first-use glosses where helpful. Annotate uncommon characters with pinyin on first use using `字（pinyin）` format — e.g. 杕杜（dì dù）、蝃蝀（dì dōng）. Do not annotate common characters.

20. **Maintain structural consistency.** All entries use the same heading level (`##`). No附录/补充 labels. 结语 at end only.

21. Cite properly:
    - Inline footnote-style markers `[¹]`, `[²]`… with a 参考文献 list at the end.
    - For text you quote verbatim, quote exactly (including chapter/回目), and give the source immediately.
    - Include an access date for web sources.

### Phase 5 — 结语 (conclusion)

22. The 结语 MUST cover every entry in the article. List all characters and summarize the naming patterns found. Do not subset — if the article has18 characters, the 结语 mentions all18.
23. Highlight the author's naming craft (曹雪芹's 用字苦心, etc.) and any commentator insights (脂砚斋批语).
24. Connect names to character fates where applicable.

### Phase 6 — Corrections doc (conditional)

25. Quality control is the goal; the corrections doc is only the evidence. If every claim verifies, **no corrections doc is created**.
26. Anything unverifiable or contradictory goes into `docs/YYMMDD-corrections-by-citation.md`. Structure per `docs/260808-corrections-by-citation.md`: 校核总表, 已修正逐条明细, 待核实清单, 引用来源清单.
27. If the article already has a corrections doc, append to it.

### Phase 7 — Post-writing citation audit

After the article is complete, verify every citation:

28. **Search each quoted sentence on the web.** Confirm it surfaces in the primary text or independently-verifiable sources.
29. **Verify exact wording.** Classical texts have variant editions. Confirm the quote matches the edition you cite.
30. **Check attribution accuracy.** Confirm the quoted line actually comes from the work you attribute it to. Misattribution is common.
31. **Apply corrections.** Fix inaccurate citations, record changes in the corrections doc, then re-check the affected section for duplication or flow breaks.

## Repo conventions (from AGENTS.md)

- Filenames: `docs/<YYMMDD>-<slug>.md`, lowercase hyphenated slug, 6-digit date prefix, no spaces.
- Images: `imgs/<YYMMDD>-<slug>.<ext>` (same date prefix). Reference as `../imgs/<file>`.
- Update `README.md` whenever articles are added, moved, or removed.
- Do not create a corrections doc unless there is something to record.

## Verification checklist (run before finishing)

- [ ] **Phase 1**: User's character list and ordering preserved — same characters, same sequence.
- [ ] **Phase 2**: Every name-source attribution has ≥2 independent reliable sources (or 1 for well-established primary-text facts).
- [ ] **Phase 3**: Every cited source was actually opened and the supporting sentence was located; no ghost citations.
- [ ] **Phase 4**: Each entry contains all three mandatory elements (背景, 链接, 赏析); no fact stated twice within the same entry.
- [ ] **Phase 5**: 结语 covers every entry in the article.
- [ ] **Phase 7**: Post-writing citation audit completed — every quote verified, exact wording confirmed, attributions checked.
- [ ] No claim from untrusted sources treated as evidence.
- [ ] Unverifiable items in corrections doc under "待核实", not asserted in the article.
- [ ] Uncommon characters annotated with pinyin on first use.
- [ ] Filename follows `YYMMDD-slug`; images referenced as `../imgs/<file>`; README in sync.
- [ ] Nothing committed unless the user explicitly asks.

## Error handling

- **User's attribution conflicts with reliable sources**: show the discrepancy and both sides' evidence; propose the fix; wait for approval.
- **Sources conflict**: record both versions in the corrections doc under "待核实"; present the conflict to the user.
- **Source is paywalled / unavailable**: rely on the other independent source and note the gap.
- **Character has no known literary source**: state this explicitly in the entry (e.g. "此名未见直接典籍出处"); do not fabricate an attribution.
- **Article is too long**: ask the user which characters to trim; do not silently cut content.
