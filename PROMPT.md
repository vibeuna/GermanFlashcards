# Ultimate Flashcards — The Full Prompt

> This document contains the exact prompt that was used to generate the **Ultimate Flashcards** Progressive Web App. It can be reused, adapted, or shared as a reference for AI-assisted app generation.

---

## The Prompt

```
"Act as an expert Full-stack Web Developer and UI/UX Designer. Create a premium,
standalone Progressive Web App (PWA) for learning German vocabulary using
spaced-repetition flashcards.

Core Functionality:

Flashcard Engine: Interactive study mode with 3D flip animations. Supports
German/Front and English/Back with example sentences.

Settings Menu (Study Management):
  - Study Direction: Allow users to toggle between 'German to English',
    'English to German', and 'Mixed/Both'.
  - Customizable Intervals: provide a detailed settings section where users
    can manually set the number of days for review intervals for the
    following grades:
      - Wrong (Review again in X days)
      - Correct (X days)
      - Semi-Easy (X days)
      - Easy (X days)
      - 1 Month (X days)
      - 2 Months (X days)
  - Danger Zone: A clearly marked section in settings with a 'Delete All Data'
    button that clears localStorage after a confirmation prompt.

Data Management:
  - Import/Export CSV files (German Word, English Translation, Example Sentence).
  - Add words manually or via OCR (Tesseract.js).
  - LocalStorage persistence and Offline support (manifest.json + Service Worker).

Design & Aesthetic Requirements:

  - Aesthetic: Modern minimalist 'Inter' font, Vibrant indigo (#6366f1) and
    pink (#ec4899) gradients, and glassmorphism.
  - Micro-interactions: Use a floating settings button (gear icon) that opens
    a sleek slide-out or modal menu.
  - Layout: Mobile-first, centered layout (max 640px) with responsive
    safe-area padding for notches.

Tech Stack:

  - Single-file HTML for structure, Vanilla CSS for styling (design tokens
    via CSS variables), and Vanilla JavaScript for logic. CDNs for
    Tesseract.js and Google Fonts."
```

## How to Reuse This Prompt

You can adapt this prompt for other language pairs by changing:
- "German" → your target language
- `#6366f1` / `#ec4899` → your preferred color palette
- The OCR language code (`deu` → `fra`, `spa`, etc.)
- The translation pair (`de|en` → `fr|en`, `es|en`, etc.)

The prompt is structured in three sections — **Functionality**, **Design**, and **Tech Stack** — which makes it easy to swap individual requirements while keeping the rest intact.
