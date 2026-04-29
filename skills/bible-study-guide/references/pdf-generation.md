# PDF Generation Guide

This document covers how to convert the HTML study guides into high-quality PDF files.

---

## Overview

The study guides are generated as self-contained HTML files with all CSS inlined. These HTML files can be:
1. Viewed directly in a browser
2. Printed to PDF via headless Chrome/Puppeteer
3. Shared as HTML files via email or messaging

---

## Method 1: Puppeteer (Recommended)

### Setup

```bash
# Install Puppeteer and download Chromium
npm install puppeteer
npx puppeteer browsers install chrome
```

### Conversion Script

```javascript
const puppeteer = require('puppeteer');
const path = require('path');

async function htmlToPdf(inputHtml, outputPdf) {
  const browser = await puppeteer.launch({
    headless: 'new',
    args: ['--no-sandbox', '--disable-setuid-sandbox']
  });

  const page = await browser.newPage();

  // Load the HTML file
  const filePath = path.resolve(inputHtml);
  await page.goto(`file://${filePath}`, {
    waitUntil: 'networkidle0'
  });

  // Generate PDF
  await page.pdf({
    path: outputPdf,
    format: 'A4',
    margin: {
      top: '16mm',
      right: '16mm',
      bottom: '16mm',
      left: '16mm'
    },
    printBackground: true  // Important: preserves colored backgrounds
  });

  await browser.close();
  console.log(`PDF saved to: ${outputPdf}`);
}

// Usage
htmlToPdf('john8_study.html', 'john8_study.pdf');
```

### Key Options

| Option | Value | Why |
|--------|-------|-----|
| `format` | `'A4'` | Standard paper size |
| `margin` | `16mm` all sides | Comfortable reading margin |
| `printBackground` | `true` | **Critical** — without this, scripture blocks, callouts, and big question cards lose their backgrounds |

---

## Method 2: Chrome CLI (Simpler)

```bash
google-chrome \
  --headless \
  --disable-gpu \
  --no-sandbox \
  --print-to-pdf="output.pdf" \
  --print-to-pdf-no-header \
  input.html
```

**Limitations:**
- Less control over margins and options
- No `printBackground` equivalent in older versions
- Works well for quick one-offs

---

## Font Setup (Optional — for Noto Sans)

If you want to use Noto Sans / Noto Sans KR web fonts for pixel-perfect rendering:

### 1. Download Fonts

```bash
mkdir -p .fonts

# Noto Sans (Latin)
curl -L -o .fonts/NotoSans-Regular.ttf \
  "https://github.com/google/fonts/raw/main/ofl/notosans/NotoSans%5Bwdth%2Cwght%5D.ttf"

# Noto Sans KR (Korean)
curl -L -o .fonts/NotoSansKR-Regular.ttf \
  "https://github.com/google/fonts/raw/main/ofl/notosanskr/NotoSansKR%5Bwght%5D.ttf"
```

### 2. Add @font-face to CSS

```css
@font-face {
  font-family: 'Noto Sans';
  src: url('/absolute/path/to/.fonts/NotoSans-Regular.ttf') format('truetype');
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: 'Noto Sans KR';
  src: url('/absolute/path/to/.fonts/NotoSansKR-Regular.ttf') format('truetype');
  font-weight: 400;
  font-style: normal;
}
```

**Important:** Use **absolute paths** in `@font-face src` URLs when generating PDFs via Puppeteer. Relative paths may not resolve correctly from the headless browser's context.

### 3. System Font Fallback

The default CSS uses a system font stack that works without downloading fonts:
```css
font-family: 'Noto Sans KR', 'Noto Sans', -apple-system, BlinkMacSystemFont,
  'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
```

On most systems:
- **macOS:** Falls back to Apple SD Gothic Neo (Korean) + SF Pro
- **Windows:** Falls back to Malgun Gothic (Korean) + Segoe UI
- **Linux:** Falls back to system sans-serif; install `fonts-noto-cjk` for Korean support

---

## Page Formatting

### CSS @page Rule (already in style.css)

```css
@page {
  size: A4;
  margin: 16mm;
}
```

### Print Media Query

```css
@media print {
  body { background: #fff; }
  .container { padding: 0; max-width: 100%; }

  .callout, .term-card, .scripture-block,
  .commentary, .question, .big-question,
  .notes-area { page-break-inside: avoid; }

  h2, h3 { page-break-after: avoid; }
  .report-header { page-break-after: avoid; }
}
```

### Color Accuracy

Both of these are set on `<html>`:
```css
-webkit-print-color-adjust: exact;
print-color-adjust: exact;
```

This ensures Chrome prints background colors and images as they appear on screen.

---

## Workflow Summary

1. **Generate HTML** — Agent creates the study guide HTML with inlined CSS
2. **Save to file** — Write to `{book}{chapter}_study.html` (e.g., `john8_study.html`)
3. **Convert to PDF** — Use Puppeteer script or Chrome CLI
4. **Verify** — Open PDF to check layout, page breaks, and Korean text rendering
5. **Deliver** — Share the PDF (and optionally the HTML) with the study group

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Korean text shows as boxes | Install `fonts-noto-cjk` or download Noto Sans KR fonts |
| Backgrounds missing in PDF | Ensure `printBackground: true` (Puppeteer) or `print-color-adjust: exact` (CSS) |
| Content cut off at page edges | Check margins are set to 16mm |
| Awkward page breaks | Add `page-break-inside: avoid` to the problematic element |
| Large scripture blocks split across pages | Consider splitting into smaller verse groups |
| Puppeteer hangs | Add `--no-sandbox --disable-setuid-sandbox` to launch args |
