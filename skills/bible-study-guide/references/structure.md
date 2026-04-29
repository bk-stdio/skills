# Study Guide Structure

Each study guide covers **one chapter** (or major section) of a biblical book and is designed for a **30–60 minute small-group discussion** with mixed audiences (believers + seekers).

---

## 1. Header

| Element | Description |
|---------|-------------|
| **Series tag** | `{{책이름}} 성경공부 · {{N}}회차` — e.g., "요한복음 성경공부 · 8회차" |
| **Title** | A creative, thematic title that captures the chapter's central idea. Never just "Chapter 8." |
| **Subtitle** | Verse range + Bible version — e.g., "요한복음 8장 전체 (1–59절) · 현대인의 성경" |

**CSS classes:** `.report-header`, `.series-tag`, `h1`, `.subtitle`

---

## 2. 지난 시간 요약 (Previous Session Recap)

- **Blue info callout** (`.callout.callout-info`)
- Icon: 📖
- Summarize the previous chapter's key points in 2–3 sentences
- Preview what's coming in this chapter (bridge sentence)

**Special case — Chapter 1:** Instead of a recap, provide a **book introduction**:
- Author, date, audience, purpose
- Major themes to watch for throughout the book
- Why this book matters for your study group

---

## 3. 목차 (Table of Contents)

- **Numbered `<ol>` list** inside `<nav class="toc">`
- Mirrors the `<h2>` sections in the document
- Typically: 핵심 단어 → 본문 I → 본문 II → (본문 III/IV) → 나눔 질문
- Include section subtitles and verse ranges in the TOC entries

---

## 4. 핵심 단어 (Key Terms)

- **3–6 terms** per chapter
- Each term rendered as a `.term-card`:
  - `.term-name`: Korean term + English/Greek equivalent in parentheses
  - `.term-def`: Contextual definition — why this word matters for THIS passage
- **Not** academic dictionary definitions. Explain relevance.
- Always include this note above the cards:

> 외울 필요 없습니다. 읽다가 모르는 단어가 나오면 여기서 찾아보세요.

---

## 5. 본문 + 해설 (Scripture Text + Commentary)

This is the main body. Split the chapter into **2–4 logical sections** based on narrative or thematic breaks.

### Each section contains:

#### a) Scripture Block (`.scripture-block`)
- Reference line (`.ref`): "요한복음 8:1–11 (현대인의 성경)"
- Verse text with superscript verse numbers (`<span class="vn">`)
- Use the configured Bible version text

#### b) Commentary Block (`.commentary`)
- Label (`.cm-label`): "배경 및 해설"
- Content should include:
  - **Historical/cultural background** — What would the original audience understand?
  - **Literary context** — How does this fit the book's argument/narrative?
  - **Theological significance** — What truth is being communicated?
  - **Cross-references** — Connections to other passages (brief, not exhaustive)

#### c) Optional Callout Boxes (`.callout.callout-warning`)
Use amber/warning callouts for:
- Textual criticism notes (e.g., John 7:53–8:11 pericope)
- Extended cultural context that needs its own box
- Difficult theological concepts that benefit from dedicated explanation
- Greek/Hebrew word studies that illuminate meaning

---

## 6. 나눔 질문 (Discussion Questions)

Three tiers using the **OIA method** (Observation → Interpretation → Application):

### 👀 본문이 뭐라고 말하고 있나요? (Observation)
- 2–3 questions
- Focus: What does the text literally say? What happened? Who said what?
- Purpose: Gets everyone reading carefully. Non-believers can answer these confidently.

### 🤔 이게 무슨 뜻인가요? (Interpretation)
- 2–3 questions
- Focus: Why did the author include this? What does it mean in context?
- Purpose: Deeper engagement. May require referencing the commentary.

### 💬 그래서 나에게 어떤 의미가 있나요? (Application)
- 2 questions
- Focus: How does this connect to my life? What changes?
- Purpose: Personal and vulnerable. Open-ended, not prescriptive.

**Question design principles:**
- Open-ended, never leading ("How does this make you feel?" not "Don't you think this is amazing?")
- Sequentially numbered (1–8 across all three sections)
- Rendered as `.question` divs with `.q-num` and `.q-text`

---

## 7. 오늘의 핵심 질문 (Big Question)

- **Dark card** (`.big-question`) with white text
- One single provocative question that captures the chapter's central tension
- Should be:
  - Memorable — sticks with people after they leave
  - Genuinely challenging — not a softball with an obvious answer
  - Universal — relevant to both believers and seekers
- Example: "진리를 안다는 것이 왜 그들을 자유하게 하지 못했을까?"

---

## 8. 메모 (Notes)

- **Dashed-border empty area** (`.notes-area`)
- For personal notes during or after discussion
- Prints as blank space in PDF — intentionally empty

---

## 9. 다음 시간 예고 (Next Session Preview)

- **Green success callout** (`.callout.callout-success`)
- Icon: 📅
- Tease the next chapter's content in 1–2 sentences
- Create anticipation without spoiling
- For the **last chapter** of a book, either:
  - Preview the next book in the series, or
  - Provide a wrap-up reflection on the whole book
