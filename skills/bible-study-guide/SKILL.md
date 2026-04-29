---
name: bible-study-guide
description: "Generate beautifully formatted Bible study guide PDFs for small group discussion. Produces self-contained HTML files (convertible to PDF) following a proven pedagogical structure: previous session recap, key terms, Scripture text with commentary, three-tier OIA discussion questions (observation → interpretation → application), a provocative Big Question, and next session preview. Designed for mixed audiences of believers and seekers. Korean (현대인의 성경) by default, English supported. Use when: user asks to create a Bible study, 성경공부 가이드, study guide for any book/chapter, small group materials, or discussion-led Bible study worksheets."
---

# Bible Study Guide Generator

Generate discussion-led Bible study guides as self-contained HTML → PDF. Each guide covers one chapter of a biblical book, designed for **30–60 minute small group sessions** with mixed audiences (believers + seekers).

## Related Skills

- **report-generator** — Use its PDF conversion workflow and Notion-style design system. This skill extends report-generator with Bible study-specific structure.
- **reformed-theology** — Use its theological method for commentary depth. This skill provides the *format*; reformed-theology provides the *substance*.

## Workflow

### 1. Scope

Confirm with the user:
- **Book & chapter** (e.g., John 8)
- **Session number** (may differ from chapter number if chapters were combined/split)
- **Language**: Korean (default) or English
- **Bible version**: 현대인의 성경 (default), 개역개정, NIV, ESV, NASB

### 2. Write Content

Using the theological method from reformed-theology skill (if available) or your own Bible knowledge:

1. Read the chapter; identify 2–4 logical sections
2. Select 3–6 key terms needing explanation
3. Write commentary per section (historical, literary, theological)
4. Craft OIA discussion questions
5. Compose the Big Question
6. Write previous session recap + next session preview

See `references/structure.md` for the 9-section pedagogical framework.

### 3. Generate HTML

Build a self-contained HTML file:
- Copy the full CSS from `references/study-styles.css` into a `<style>` tag
- Follow the structure in `references/template.html`
- See `references/design-guide.md` for component CSS classes
- See `references/theology-guide.md` for commentary and question guidelines
- Save as `{book}{chapter}_study.html`

### 4. Convert to PDF

```bash
# Chrome CLI (simplest)
google-chrome --headless --disable-gpu --no-sandbox \
  --print-to-pdf="output.pdf" --print-to-pdf-no-header input.html

# Or Puppeteer (more control) — see references/pdf-generation.md
```

## Example

See `examples/john8.md` for a walkthrough of John 8 showing the complete output structure, commentary style, and question design.

## Configuration

| Option | Default | Alternatives |
|--------|---------|-------------|
| Language | Korean | English |
| Bible version | 현대인의 성경 | 개역개정, NIV, ESV, NASB, NLT |
| Questions | 3 / 3 / 2 | Adjustable per tier |
| Session length | 30–60 min | Affects question count |

## Tips

- **Chapter 1**: Replace recap with book introduction (author, date, themes, purpose)
- **Last chapter**: Next preview becomes series wrap-up or next book preview
- **Long chapters**: Split across 2 sessions
- **Short chapters**: Combine adjacent chapters (e.g., 2 John + 3 John)
