# Visual Design Guide

Clean, Notion-style design optimized for both screen viewing and PDF printing.

---

## Color Palette

| Token | Hex | Usage |
|-------|-----|-------|
| Primary accent | `#2563EB` | Header border, h1, term names, question section headers |
| Text primary | `#1A1A1A` | h2, body headings |
| Text body | `#1E293B` | Verse text, commentary text |
| Text secondary | `#374151` | Commentary text, term definitions |
| Text subtle | `#6B7280` | Series tag, subtitle, labels |
| Text muted | `#9CA3AF` | Footer, verse numbers, notes label |
| Border | `#E5E7EB` | Section dividers, term card borders, toc border |
| Background | `#FFFFFF` | Page |
| Scripture bg | `#F8FAFC` | Scripture blocks |
| Commentary bg | `#FAFBFF` | Commentary blocks |
| Dark card | `#1E293B` | Big Question background |

## Callout Types

| Type | Background | Border | Icon | Use for |
|------|-----------|--------|------|---------|
| Info (blue) | `#EFF6FF` | `#BFDBFE` | 📖 / 🔍 | Previous recap, context boxes |
| Warning (amber) | `#FFFBEB` | `#FDE68A` | 📝 / ⚠️ | Textual criticism, difficult passages |
| Success (green) | `#F0FDF4` | `#BBF7D0` | 📅 | Next session preview |

## Typography

**Font stack:** `'Noto Sans KR', 'Noto Sans', -apple-system, BlinkMacSystemFont, sans-serif`

| Element | Size | Weight |
|---------|------|--------|
| html base | 14.5px | — |
| h1 (title) | 25px | 700 |
| h2 (sections) | 19px | 700 |
| h3 (subsections) | 15.5px | 700 |
| Body / verse text | 13.5–14px | 400 |
| Callout text | 13px | 400 |
| Term definitions | 13px | 400 |
| Series tag | 11px | 600 |
| Verse numbers (.vn) | 10px | 700 |
| Commentary label | 10px | 700 |

**Line heights:** body 1.8 · verses 1.9 · commentary 1.7 · callouts 1.7

## Layout

- Container: `max-width: 700px`, centered
- Header: `border-bottom: 2px solid #2563EB`
- Sections: `border-top: 1px solid #E5E7EB` on h2 (except first)
- Spacing between sections: `margin-top: 36px` on h2

## Key Components

**Scripture block:** Light background (`#F8FAFC`), 1px border, rounded 10px. Verse numbers are superscript in subtle gray (`#94A3B8`).

**TOC:** Light gray background (`#F9FAFB`), 1px border, rounded 8px. Custom counter-based numbering — numbers are blue (`#2563EB`).

**Commentary block:** Very light purple (`#FAFBFF`), 1px border, rounded 8px. Label is uppercase, small, **indigo-colored** (`#6366F1`, NOT gray).

**Term cards:** White background, 1px gray border, rounded 8px. Term name in blue (`#2563EB`), bold.

**Question numbers:** Blue circle (`#2563EB` bg, white text), 22px diameter, inline-flex centered.

**Big Question:** Dark slate (`#1E293B`), white text, centered, 16px font, rounded 10px. Label is small uppercase in light gray (`#94A3B8`).

**Notes area:** Dashed border (`1px dashed #D1D5DB`), min-height 70px, rounded 8px.

## Print Rules

```css
@media print {
  .container { max-width: 100%; padding: 0; }
  h2, h3 { page-break-after: avoid; }
  .scripture-block, .callout, .commentary,
  .question, .big-question { page-break-inside: avoid; }
}
@page { margin: 16mm; }
```

Always set on html: `-webkit-print-color-adjust: exact; print-color-adjust: exact;`
