# Visual Design Guide

The study guide design system is optimized for readability in both screen and print (PDF) contexts. It uses a clean, modern look with a constrained color palette and generous whitespace.

---

## Color Palette

| Token | Hex | Usage |
|-------|-----|-------|
| **Primary** | `#2563EB` | Headers, term names, verse numbers, info callout accents |
| **Text** | `#1A1A1A` | Body headings |
| **Body text** | `#1E293B` | Verse text, commentary, question text |
| **Secondary text** | `#374151` | TOC items, term definitions |
| **Subtle gray** | `#6B7280` | Series tag, subtitle, references, labels |
| **Muted gray** | `#9CA3AF` | Footer text, notes label |
| **Border** | `#E5E7EB` | Section dividers, term card borders |
| **Light border** | `#F3F4F6` | Question separators |
| **Background** | `#FFFFFF` | Page background |
| **Scripture bg** | `#F1F5F9` | Scripture block background |
| **Commentary bg** | `#FAFBFF` | Commentary block background |
| **Dark card** | `#1E293B` | Big Question background |
| **Dark card text** | `#FFFFFF` | Big Question text |
| **Dark card label** | `#94A3B8` | Big Question label text |

---

## Callout Types

Three callout styles, each with a colored left border and tinted background:

### Info (Blue)
- Background: `#EFF6FF`
- Border-left: `4px solid #2563EB`
- Strong text color: `#1D4ED8`
- **Use for:** Previous session recap, book introductions, general notes

### Warning (Amber)
- Background: `#FFFBEB`
- Border-left: `4px solid #D97706`
- Strong text color: `#B45309`
- **Use for:** Textual criticism, cultural context boxes, difficult passages

### Success (Green)
- Background: `#F0FDF4`
- Border-left: `4px solid #16A34A`
- Strong text color: `#15803D`
- **Use for:** Next session preview

### Callout Structure
```html
<div class="callout callout-info">
  <div class="callout-icon">📖</div>
  <div class="callout-content">
    <strong>Title</strong>
    <p>Content...</p>
  </div>
</div>
```
- Layout: flex row with 12px gap
- Icon: 20px font-size, flex-shrink: 0
- Border-radius: 10px
- Padding: 16px 18px

---

## Key Components

### Scripture Block
- Background: `#F1F5F9` (light blue-gray)
- Border-radius: 10px
- Padding: 20px 22px
- Reference line: 12px, semi-bold, gray
- Verse numbers: `<span class="vn">` — 10px, bold, blue, superscript
- Verse text: 14px, `#1E293B`, line-height 1.9

### Term Cards
- Background: white with `#E5E7EB` border
- Border-radius: 8px
- Padding: 14px 18px
- Term name: 15px, bold, `#2563EB`
- Definition: 13.5px, `#374151`
- Margin-bottom: 10px between cards

### Commentary Block
- Background: `#FAFBFF` (very light purple)
- Border-radius: 10px
- Padding: 20px 22px
- Label: 12px, bold, uppercase, gray, letter-spacing 0.06em
- Text: 14px, `#1E293B`, line-height 1.85

### Discussion Questions
- Section heading: `<h3>` with emoji prefix
- Each question: flex row with `.q-num` circle (26px, blue on light-blue bg) + `.q-text`
- Questions separated by light border-bottom (`#F3F4F6`)

### Big Question
- Background: `#1E293B` (dark slate)
- Text: white, 19px, bold
- Label: 11px, uppercase, `#94A3B8`
- Border-radius: 12px
- Padding: 28px 24px
- Text-align: center

### Notes Area
- Border: `2px dashed #D1D5DB`
- Min-height: 120px
- Border-radius: 10px
- Label: 12px, semi-bold, `#9CA3AF`, uppercase

---

## Typography

### Font Stack
```css
font-family: 'Noto Sans KR', 'Noto Sans', -apple-system, BlinkMacSystemFont,
  'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
```

### Sizes
| Element | Size |
|---------|------|
| Base (html) | 14.5px |
| h1 (title) | 25px |
| h2 (sections) | 19px |
| h3 (sub-sections) | 16px |
| Body text | 14px |
| Callouts | 13.5px |
| Term defs | 13.5px |
| References | 12px |
| Series tag | 11px |
| Verse numbers | 10px |

### Line Heights
- Body: 1.8
- Verse text: 1.9
- Commentary: 1.85
- Callouts: 1.75
- Questions: 1.7

---

## Layout

- Container: `max-width: 700px`, centered, `padding: 36px 0`
- Sections separated by `border-top: 1px solid #E5E7EB` on `h2`
- Header has `border-bottom: 2px solid #2563EB`
- Footer: centered, 11.5px, `#9CA3AF`, with top border

---

## Print / PDF Rules

```css
@page {
  size: A4;
  margin: 16mm;
}

@media print {
  body { background: #fff; }
  .container { padding: 0; max-width: 100%; }

  /* Prevent awkward page breaks */
  .callout, .term-card, .scripture-block,
  .commentary, .question, .big-question,
  .notes-area { page-break-inside: avoid; }

  h2, h3 { page-break-after: avoid; }
  .report-header { page-break-after: avoid; }
}
```

Key print considerations:
- `print-color-adjust: exact` on `<html>` to preserve backgrounds
- All backgrounds and colors print as-is
- No external resources (fonts via system stack, CSS inlined)
- Page breaks avoided inside key blocks
