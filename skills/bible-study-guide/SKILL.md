---
name: bible-study-guide
description: "Generate beautifully formatted Bible study guide PDFs for small group discussion. Produces self-contained HTML files (convertible to PDF) with a proven pedagogical structure: previous session recap, key terms, Scripture text with verse-by-verse commentary, three-tier OIA discussion questions (observation → interpretation → application), a provocative Big Question, and next session preview. Designed for mixed audiences of believers and seekers. Korean (현대인의 성경) by default, English supported. Fully self-contained — no other skills required. Use when: user asks to create a Bible study, 성경공부 가이드, study guide for [book/chapter], small group materials, discussion-led Bible study worksheets, or seeker-friendly study materials."
---

# Bible Study Guide Generator

Generate discussion-led Bible study guides as self-contained HTML → PDF. Each guide covers one chapter of a biblical book, designed for **30–60 minute small group sessions** with mixed audiences (believers + seekers).

This skill is fully self-contained. No other skills are required.

## Workflow

### 1. Scope

Confirm with the user:
- **Book & chapter** (e.g., John 8)
- **Session number** in the series (may differ from chapter if chapters were combined/split)
- **Language**: Korean (default) or English
- **Bible version**: 현대인의 성경 (default), 개역개정, NIV, ESV, NASB

### 2. Write Content

Follow the 9-section structure in `references/structure.md` and the theological approach in `references/theology-guide.md`. The quality of the commentary is what makes these guides valuable — read both references before writing.

### 3. Generate HTML

Build a self-contained HTML file:
- Copy the full CSS from `references/study-styles.css` into a `<style>` tag
- Follow the HTML patterns in `references/template.html`
- Reference `references/design-guide.md` for component CSS classes
- Save as `{book}{chapter}_study.html`

**Critical:** The CSS must be inlined. The HTML must work as a standalone file.

### 4. Convert to PDF

```bash
# Chrome CLI
google-chrome --headless --disable-gpu --no-sandbox \
  --print-to-pdf="output.pdf" --print-to-pdf-no-header input.html

# Or Puppeteer — see references/pdf-generation.md
```

## Configuration

| Option | Default | Alternatives |
|--------|---------|-------------|
| Language | Korean | English |
| Bible version | 현대인의 성경 | 개역개정, NIV, ESV, NASB, NLT |
| Questions | 3 / 3 / 2 | Adjustable per tier |

## Tips

- **Chapter 1** of any book: Replace recap with book introduction (author, date, themes, purpose)
- **Last chapter**: Next preview becomes series wrap-up
- **Long chapters**: Split across 2 sessions
- **Short chapters**: Combine adjacent ones (e.g., 2 John + 3 John)

## Resources

| File | When to read |
|------|-------------|
| `references/structure.md` | Always — the 9-section pedagogical framework |
| `references/theology-guide.md` | Always — commentary method, question design, audience sensitivity |
| `references/study-styles.css` | When generating HTML — copy into `<style>` tag |
| `references/template.html` | When generating HTML — reference for structure |
| `references/design-guide.md` | When generating HTML — component CSS classes |
| `references/pdf-generation.md` | When converting to PDF |
| `examples/john3-complete.html` | To see a complete, real output at full quality |
| `examples/john8-walkthrough.md` | To understand the methodology behind each section |
