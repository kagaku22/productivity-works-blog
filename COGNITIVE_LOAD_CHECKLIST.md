# Cognitive Load Reduction Checklist
## productivity-works-blog — 122 Articles (Hugo + PaperMod)
### Research compiled: 2026-05-14

This checklist is designed to be applied **programmatically** to all 122 Markdown articles.
Each item includes the rationale, the concrete rule, and how to implement it in Hugo/PaperMod Markdown.

---

## 1. PARAGRAPH LENGTH

**Rule:** Max 3 sentences per paragraph, target 2.

**Rationale:** Working memory can hold 4±1 chunks. Long paragraphs force readers to re-read
to locate the main idea. Jakob Nielsen's eye-tracking studies show users scan in F-patterns;
walls of text are abandoned. Yoast readability guidelines enforce ≤150 words per paragraph.

**Implementation:**
- Split any paragraph with 4+ sentences at the nearest logical boundary.
- Insert a blank line between every paragraph (already standard in Markdown, but enforce it).
- Never let a single paragraph exceed ~75 words.

---

## 2. SUBHEADINGS FREQUENCY

**Rule:** At least one H2 or H3 every 250–300 words. No section longer than 300 words without a subheading.

**Rationale:** Subheadings act as "cognitive signposts." Readers scan headings first (57% readability
improvement per Nielsen). In PaperMod, H2 anchors also feed the auto-generated ToC.

**Implementation:**
- Count words between consecutive headings. If > 300, split with a new H3.
- Headings must be descriptive and front-load the key idea ("Short paragraphs reduce bounce" not "Paragraph tips").
- Avoid consecutive H2s with no body text between them.
- Use sentence case, not title case (reads more naturally at speed).

**Heading hierarchy:**
```
H1  — Article title (set by front matter, never repeat in body)
H2  — Major sections (3–6 per article)
H3  — Subsections within an H2 (0–3 per H2)
H4+ — Avoid entirely
```

---

## 3. WHITE SPACE AND SECTION BREAKS

**Rule:** Add a horizontal rule (`---`) before every H2. Add a blank line after every list, code block, or blockquote.

**Rationale:** White space is "visual breathing room." It signals a complete thought and prevents
cognitive blurring between topics. Mobile readers especially benefit because short viewports
make wall-of-text even more pronounced.

**Implementation:**
- Between major H2 sections: `\n---\n\n## Next Section`
- After every bullet list or numbered list: one blank line before next paragraph.
- Do NOT add `---` before H3 (too much fragmentation).
- Ensure the final section ends with a blank line before the CTA block.

---

## 4. BOLD AND ITALIC USAGE PATTERNS

**Rule:**
- **Bold** (`**text**`): 1–3 key phrases per section. Bold the single most important takeaway per paragraph.
- *Italic* (`*text*`): Use only for titles, technical terms on first use, or genuine emphasis — max 1 per paragraph.
- Never bold entire sentences. Never bold more than 6 words at once.

**Rationale:** Bold text creates a "scannable skeleton" — a reader who reads only the bolded phrases
should still grasp the core message. Overuse destroys this effect by making everything equally loud.

**Implementation:**
- Scan each paragraph: if no word or phrase is bolded, identify the single most critical term and bold it.
- If more than 3 bold phrases exist in one paragraph, remove the least important ones.
- Italics: apply to foreign words, book/article titles, and first occurrence of a specialized term.

---

## 5. LISTS vs. PROSE

**Rule:**
- Use bullet lists for 3+ parallel items with no required order.
- Use numbered lists for sequential steps or ranked items.
- Use prose (sentences) for narrative, causal explanations, or fewer than 3 items.
- Maximum list depth: 2 levels (bullets inside bullets). Never 3 levels.

**Rationale:** Lists reduce extraneous cognitive load because readers process each item independently.
The psychological "promise of finitude" lowers anxiety ("I can see how many items there are").
Parallel grammatical structure within lists reduces processing time by ~20% (writing research).

**Implementation:**
- Each bullet item: start with a verb or noun (parallel structure). Max ~15 words per bullet.
- If a bullet needs a sub-sentence of explanation, consider prose instead.
- Convert any sentence like "There are three things to remember: A, B, and C" into a bullet list.
- Do not convert narrative paragraphs that tell a story — prose is correct there.

---

## 6. TL;DR / KEY TAKEAWAYS SECTIONS

**Rule:** Every article must have either:
- A **TL;DR block at the top** (immediately after the intro paragraph), OR
- A **Key Takeaways section at the bottom** (immediately before the CTA), OR
- Both for articles over 1,500 words.

**Format for TL;DR (top):**
```markdown
> **TL;DR:** [1–2 sentence summary of the article's core value proposition.]
```
Rendered as a blockquote in PaperMod — visually distinct without custom shortcodes.

**Format for Key Takeaways (bottom):**
```markdown
---

## Key Takeaways

- [Core point 1 — actionable]
- [Core point 2 — actionable]
- [Core point 3 — actionable]
```

**Rationale:** 73% of readers decide within 15 seconds whether to continue reading. A TL;DR
captures the "decision-ready scanners" before they bounce. Takeaways at the bottom reward
readers who finish and give them a memorable exit.

---

## 7. TABLE OF CONTENTS (ToC)

**Rule:** Enable ToC for every article over 800 words.

**PaperMod front matter:**
```yaml
---
ShowToc: true
TocOpen: false
---
```

- `ShowToc: true` — renders the ToC.
- `TocOpen: false` — ToC is collapsed by default on mobile (prevents screen domination).
- For articles < 800 words: `ShowToc: false` (a ToC on a short article adds noise, not value).

**Rationale:** ToC allows non-linear navigation. Readers who arrive via search often want a
specific sub-section. Providing instant jump links reduces "where is the thing I need?" frustration.
PaperMod generates ToC from H2/H3 headings automatically — so fixing headings (rule 2) also improves ToC quality.

**Implementation:**
- Add `ShowToc: true` and `TocOpen: false` to front matter of all articles > 800 words.
- Ensure every H2 heading is meaningful (it will appear verbatim in the ToC).

---

## 8. VISUAL PLACEHOLDERS (No real images — use Markdown-native elements)

Since the blog cannot host real images, use these in order of impact:

### 8a. Horizontal Rules as Visual Separators
```markdown
---
```
Already in rule 3. Primary visual break tool.

### 8b. Blockquotes for Key Insights
```markdown
> "The single biggest productivity gain comes not from doing more, but from eliminating the right things."
```
PaperMod styles blockquotes with a left border — high visual contrast without images.

### 8c. Code Blocks for Examples, Templates, or Frameworks
```markdown
```
Step 1: Define the outcome
Step 2: Identify blockers
Step 3: Execute the smallest next action
```
```
Even for non-code content, fenced code blocks create a visually distinct "reference panel."

### 8d. ASCII / Text Diagrams for Simple Flows
```markdown
```
[Input] --> [Process] --> [Output]
   |                        |
[Review] <----- [Feedback] -+
```
```

### 8e. Callout-style Bold Blockquotes (PaperMod compatible)
```markdown
> **Key Insight:** [One sentence that is the most important thing in the section.]
```

### 8f. NO Emojis in Body Text
- Do not use emojis as bullet prefixes or section markers.
- Exception: the article's meta description (`description:` in front matter) may use 1 emoji for CTR in search results.
- Rationale: emojis add extraneous cognitive load on technical/professional content and break screen readers.

---

## 9. CALL-TO-ACTION (CTA) PLACEMENT

**Rule:** Every article must have exactly **3 CTA touchpoints**:

| Position | Type | Format |
|---|---|---|
| After intro (above fold) | Soft CTA | Inline text link to related article or resource |
| Mid-article (50–60% mark) | Medium CTA | Blockquote-style prompt |
| End of article | Hard CTA | Dedicated H2 section |

**Format for mid-article CTA:**
```markdown
> **Found this useful?** Share it with your team or [explore related productivity techniques](../related-post/).
```

**Format for end CTA (hard):**
```markdown
---

## What to Do Next

If this resonated, the natural next step is [specific action].
[Read: Article Title](../link/) — [one sentence on what they will gain].
```

**Rationale:**
- CTAs above the fold: 57% of users spend most time in this viewport area, 91% chance of being seen.
- Mid-article CTAs: integrated CTAs deliver up to 121% boost in engagement vs. sidebar/banner.
- End CTAs: capture "decision-ready" readers who have consumed the full piece.
- 3 placements > 1 because different readers convert at different depths.

---

## 10. INTRODUCTION STRUCTURE

**Rule:** Every intro must follow this 3-part structure in ≤ 100 words:

1. **Hook** — 1 sentence that names the reader's pain or situation.
2. **Promise** — 1–2 sentences stating what they will learn/gain.
3. **Bridge** — 1 sentence transitioning into the first H2.

**Example:**
```
Managing your inbox shouldn't feel like a second job. [Hook]
In this guide you will learn three inbox systems used by high-performers to achieve zero unread messages by Friday. [Promise]
Let's start with the most overlooked setting in any email client. [Bridge]
```

**Bad intro pattern to eliminate:**
- Do not start with "In today's fast-paced world..."
- Do not start with a dictionary definition.
- Do not bury the promise in paragraph 3.

---

## 11. SENTENCE COMPLEXITY

**Rule:**
- Target Flesch Reading Ease score of 60–70 (plain English, accessible to general audience).
- Max sentence length: 25 words. Flag and split any sentence over 30 words.
- Prefer active voice. Passive constructions add ~15% processing time.
- Avoid nominalizations: "make a decision" → "decide"; "provide assistance" → "help".

**Implementation (heuristics for programmatic detection):**
- Sentences containing "which," "that," "who" + subordinate clause: consider splitting.
- Sentences with 3+ commas: almost always splittable.
- Any sentence starting with "It is important to note that" — delete the preamble.

---

## 12. FRONT MATTER COMPLETENESS (PaperMod)

Every article must have this complete front matter block:

```yaml
---
title: "[Descriptive title with keyword]"
date: YYYY-MM-DD
description: "[1–2 sentence summary for meta/OG. Include primary keyword.]"
tags: ["tag1", "tag2"]
ShowToc: true          # true for >800 words, false for shorter
TocOpen: false
ShowReadingTime: true
ShowWordCount: true
ShowBreadCrumbs: true
---
```

**Rationale:**
- `ShowReadingTime: true` — sets reader expectations, reduces "how long is this?" anxiety.
- `ShowWordCount: true` — secondary signal for depth.
- `description:` — used by PaperMod for the article card summary and meta tags.

---

## SUMMARY: QUICK AUDIT RULES (Programmatic)

Apply these checks to each `.md` file in the `content/posts/` directory:

| # | Check | Threshold | Action |
|---|---|---|---|
| 1 | Paragraph word count | > 75 words | Split paragraph |
| 2 | Words between headings | > 300 | Insert new H3 |
| 3 | H2 count | < 3 for articles > 600w | Add missing sections |
| 4 | Bold phrases per paragraph | 0 | Add 1 bold phrase |
| 5 | Bold phrases per paragraph | > 3 | Remove excess |
| 6 | Has TL;DR or Key Takeaways | Missing | Add appropriate block |
| 7 | ShowToc in front matter | Missing + >800w | Add `ShowToc: true` |
| 8 | Has end CTA section | Missing | Add "What to Do Next" H2 |
| 9 | Has description in front matter | Missing | Write 1–2 sentence summary |
| 10 | Intro length | > 120 words | Trim to Hook+Promise+Bridge |
| 11 | Sentence word count | > 30 words | Flag for manual split |
| 12 | `---` before each H2 | Missing | Insert horizontal rule |

---

## SOURCES

- [Five principles to reduce cognitive load | David R Oliver, Medium](https://medium.com/@davidroliver/five-principles-to-reduce-cognitive-load-and-how-to-apply-them-60f78276169d)
- [How to Reduce Cognitive Load: 9 Best Strategies — Mendi.io](https://www.mendi.io/blogs/brain-health/how-to-reduce-cognitive-load-9-best-strategies)
- [Design Principles for Reducing Cognitive Load | Marvel Blog](https://marvelapp.com/blog/design-principles-reducing-cognitive-load/)
- [Blog Post Formatting Best Practices: Complete Guide | Automateed](https://www.automateed.com/blog-post-formatting-best-practices)
- [How to Format a Blog Post in 2026 | Friday Website Builder](https://www.fridaywebsitebuilder.com/blog/blog-format)
- [Blog Post Formatting: Boost Readability & SEO | NotionSender](https://www.notionsender.com/blog/post/blog-post-formatting)
- [How to Format a Blog Post: 16 Quick Tips | Blogging Explorer](https://bloggingexplorer.com/how-to-format-a-blog-post/)
- [5 Tips for Writing Readable Blog Posts | Yoast](https://yoast.com/5-tips-improve-readability-blog-post/)
- [13 Ways to Improve Blog Readability | WordPress.com](https://wordpress.com/go/content-blogging/13-ways-to-improve-blog-readability/)
- [Writing for Skimmers: Formatting that Boosts Readability | Kontent.ai](https://kontent.ai/blog/guide-to-formatting-that-boosts-readability/)
- [18 Ways to Create Scannable Content | ProBlogger](https://problogger.com/create-scannable-content/)
- [A complete guide to scannable blog writing | eesel.ai](https://www.eesel.ai/blog/scannable-blog-writing)
- [Best Practices for Structuring Blog Content for SEO and AI | Avintiv Media](https://avintivmedia.com/blog/best-practices-for-structuring-blog-content-for-seo-and-ai/)
- [PaperMod Variables / Front Matter | adityatelange.github.io](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-variables/)
- [PaperMod Features | GitHub Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/Features)
- [Optimal CTA Placement Strategies | Bliss Drive](https://www.blissdrive.com/cro/optimal-call-to-action-placement-strategies-revealed/)
- [CTA Best Practices to Increase Conversions | Contentsquare](https://contentsquare.com/blog/cta-best-practices/)
- [25 New CTA Statistics in 2026 | WiserNotify](https://wisernotify.com/blog/call-to-action-stats/)
