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

---

## What the AI Generated

| File | Lines | Purpose |
|------|-------|---------|
| `index.html` | ~1,700 | Single-file app containing all HTML structure, CSS styling, and JavaScript logic |
| `manifest.json` | 63 | PWA manifest for app installability (name, icons, theme, orientation) |
| `service-worker.js` | 97 | Offline cache-first strategy for all app assets and CDN resources |
| `generate-icons.html` | 72 | Utility page to generate/download all PWA icon sizes with branded gradient |
| `icons/` | 12 files | PNG icons at sizes: 16, 32, 72, 96, 128, 144, 152, 167, 180, 192, 384, 512 |

---

## Key Design Decisions Made by the AI

### 1. Glassmorphism Implementation
The prompt said "glassmorphism" — the AI interpreted this as:
- `backdrop-filter: blur(20px)` on all card containers
- Semi-transparent white backgrounds (`rgba(255, 255, 255, 0.72)`)
- Subtle white borders (`rgba(255, 255, 255, 0.4)`)
- Layered box-shadows with a colored glow effect

### 2. Animated Background
Rather than a static gradient, the AI added a `400% 400%` background-size with a 20-second `gradientShift` keyframe animation that slowly moves through indigo, pink, purple, and blue tones.

### 3. Floating Action Button (FAB)
The "floating settings button" was implemented as a fixed-position circular button (`56px`) in the bottom-right corner with:
- Indigo-to-pink gradient matching the app theme
- `rotate(30deg)` on hover for a playful micro-interaction
- `rotate(180deg)` on the gear icon when the settings modal is open

### 4. 3D Flashcard
The card flip uses:
- `perspective: 1500px` on the container
- `transform-style: preserve-3d` on the card
- `rotateY(180deg)` with a `0.7s cubic-bezier(0.4, 0, 0.2, 1)` transition
- Double `requestAnimationFrame` to prevent flash-of-flip when switching cards

### 5. Spaced Repetition Model
A simple but effective interval-based system:
- Each card tracks `level` (0–10), `nextReview`, and `lastReview`
- Cards without a `nextReview` date are always "due"
- Review grades increment the level by 0–4 depending on difficulty
- All intervals are user-configurable in Settings (1–365 days)

### 6. OCR Pipeline
The scan feature chains three steps:
1. **Camera** → `getUserMedia` with `facingMode: 'environment'`
2. **OCR** → `Tesseract.recognize()` with German (`deu`) language data
3. **Translation** → MyMemory free API (`de|en` language pair)

---

## How to Reuse This Prompt

You can adapt this prompt for other language pairs by changing:
- "German" → your target language
- `#6366f1` / `#ec4899` → your preferred color palette
- The OCR language code (`deu` → `fra`, `spa`, etc.)
- The translation pair (`de|en` → `fr|en`, `es|en`, etc.)

The prompt is structured in three clear sections — **Functionality**, **Design**, and **Tech Stack** — which makes it easy to swap individual requirements while keeping the rest intact.
