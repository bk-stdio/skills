# Study Guide Structure — 9 Sections

Each guide covers one chapter, designed for 30-60 minute small group discussion.

---

## 1. Header

```html
<header class="report-header">
  <div class="series-tag">요한복음 성경공부 · 3회차</div>
  <h1>다시 태어나야 한다</h1>
  <p class="subtitle">요한복음 3장 전체 (1–36절) · 현대인의 성경</p>
</header>
```

- **Series tag:** `{책이름} 성경공부 · {N}회차`
- **Title:** Creative and thematic — captures the chapter's central idea. NEVER just "Chapter 3."
  - Good: "다시 태어나야 한다" / "아브라함이 나기 전부터 내가 있다"
  - Bad: "요한복음 3장" / "니고데모의 이야기"
- **Subtitle:** Verse range + Bible version

## 2. 지난 시간 요약 (Previous Session Recap)

Blue info callout with 📖 icon. 2-3 sentences on previous chapter + 1 bridge sentence teasing this chapter.

```html
<div class="callout callout-info">
  <div class="callout-icon">📖</div>
  <div class="callout-content">
    <strong>지난 시간 요약</strong>
    <p>Summary of previous chapter... Bridge sentence about what's coming.</p>
  </div>
</div>
```

**Chapter 1 special case:** Replace with book introduction — author, date, audience, themes, purpose.

## 3. 목차 (Table of Contents)

```html
<nav class="toc">
  <h2>목차</h2>
  <ol>
    <li>핵심 단어</li>
    <li>본문 I — {Section title} ({verse range})</li>
    <li>본문 II — {Section title} ({verse range})</li>
    <li>나눔 질문</li>
  </ol>
</nav>
```

Mirrors the h2 sections. Typically: 핵심 단어 → 2-4 본문 sections → 나눔 질문.

## 4. 핵심 단어 (Key Terms)

3-6 terms. Always include this note first:

```html
<p style="font-size:12.5px; color:#6B7280; margin-bottom:10px;">
  외울 필요 없습니다. 읽다가 모르는 단어가 나오면 여기서 찾아보세요.
</p>
```

Each term as a card:

```html
<div class="term-card">
  <div class="term-name">거듭남 (Born Again)</div>
  <p class="term-def">Contextual definition — why this word matters for THIS passage...</p>
</div>
```

- Korean name + English (or Greek/Hebrew) in parentheses
- NOT dictionary definitions — explain relevance to this chapter
- Include Greek/Hebrew only when it genuinely illuminates (e.g., ἄνωθεν means both "again" AND "from above")

## 5. 본문 + 해설 (Scripture Text + Commentary)

This is the core. Split the chapter into **2-4 logical sections** by narrative/thematic breaks.

Each section:

### a) Section heading
```html
<h2>2. 본문 I — 니고데모와의 대화: 거듭남</h2>
```

### b) Optional context callout (before scripture, when needed)
```html
<div class="callout callout-info">
  <div class="callout-icon">🔍</div>
  <div class="callout-content">
    <strong>니고데모는 누구?</strong>
    <p>Background context that helps the reader before reading the text...</p>
  </div>
</div>
```

### c) Scripture block
```html
<div class="scripture-block">
  <span class="ref">요한복음 3:1–15 (현대인의 성경)</span>
  <div class="verse">
    <p><span class="vn">1</span>바리새파 사람 중에 니고데모라는...</p>
    <p><span class="vn">2</span>그가 어느 날 밤...</p>
  </div>
</div>
```

- Include the FULL text of the Bible version for the verse range
- Verse numbers as `<span class="vn">` superscript
- Group verses into logical paragraphs (not one per verse)

### d) Commentary block
```html
<div class="commentary">
  <div class="cm-label">배경 및 해설</div>
  <p><strong>"Key phrase" (verse#)</strong> — Explanation...</p>
  <p><strong>Question or statement</strong> — Deeper insight...</p>
</div>
```

See `theology-guide.md` for commentary voice and content guidelines.

### e) Optional warning callout (textual criticism, difficult passages)
```html
<div class="callout callout-warning">
  <div class="callout-icon">📝</div>
  <div class="callout-content">
    <strong>본문 비평 참고</strong>
    <p>Textual criticism note...</p>
  </div>
</div>
```

## 6. 나눔 질문 (Discussion Questions)

Three tiers, numbered sequentially 1-8:

```html
<div class="question-section">
  <h3>👀 본문이 뭐라고 말하고 있나요?</h3>
  <div class="question">
    <span class="q-num">1</span>
    <span class="q-text">Question text with verse references...</span>
  </div>
</div>

<div class="question-section">
  <h3>🤔 이게 무슨 뜻인가요?</h3>
  <!-- questions 4-6 -->
</div>

<div class="question-section">
  <h3>💬 그래서 나에게 어떤 의미가 있나요?</h3>
  <!-- questions 7-8 -->
</div>
```

See `theology-guide.md` for question design principles.

## 7. 오늘의 핵심 질문 (Big Question)

```html
<div class="big-question">
  <div class="label">오늘의 핵심 질문</div>
  <div class="bq-text">Provocative question...<br><br>Use line breaks for dramatic pacing.</div>
</div>
```

One question. See `theology-guide.md` for design principles.

## 8. 메모 (Notes)

```html
<div class="notes-area">
  <div class="notes-label">메모</div>
</div>
```

Empty space for personal notes. Prints as blank area in PDF.

## 9. 다음 시간 예고 (Next Session Preview)

```html
<div class="callout callout-success">
  <div class="callout-icon">📅</div>
  <div class="callout-content">
    <strong>다음 시간 예고</strong>
    <p>1 teaser sentence + 1 hook that creates anticipation.</p>
  </div>
</div>
```

**Last chapter:** Either preview the next book or provide a series wrap-up reflection.

## Footer

```html
<footer class="report-footer">
  <p>{책이름} 성경공부 · {N}회차 · {책이름} {장}장</p>
</footer>
```
