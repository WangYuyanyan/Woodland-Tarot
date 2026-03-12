# Development Log — Woodland Astral Tarot

A record of the prompt engineering process used to build this project, from initial scaffold to final polish. Each step reflects an iterative conversation with an AI coding assistant, with architecture decisions, UX judgment, and all visual design remaining my own.

---

## Step 1 — Base Structure & 3D UI

**Goal:** Establish the core data model and visual foundation.

> "Please help me write a tarot card drawing app in plain HTML/CSS/JS. Requirements: deep green retro Art Nouveau style, define a data structure for all 78 tarot cards (with Chinese and English names). Implement a 3D card carousel using CSS `transform` to arrange cards in an arc, with left/right scrolling."

**Outcome:** Working 3D carousel with card data structure. Major Arcana (ar00–ar21) and Minor Arcana with suit/rank naming convention established.

**Card naming convention defined:**
- Major Arcana: `ar00` to `ar21`
- Minor Arcana: `{suit}{rank}` — suits are `cu` (Cups), `pe` (Pentacles), `sw` (Swords), `wa` (Wands); ranks are `ac`, `02`–`10`, `pa`, `kn`, `qu`, `ki`
- Asset path: `assets/tarot/pkt/`

---

## Step 2 — Hand Gesture Control

**Goal:** Replace mouse/touch with camera-based gesture input.

> "Building on the previous code, integrate MediaPipe Hands. Add a camera preview in the bottom right. Gesture logic: hand positioned left/right controls carousel scrolling; fist held for 1.2 seconds in the center selects the current card. Include hand cursor tracking."

**Outcome:** Gesture state machine with three zones (scroll-left, select, scroll-right), fist hold timer with progress ring, hand landmark cursor overlay.

---

## Step 3 — Canvas Background & Web Audio

**Goal:** Build atmosphere without loading external media files.

> "Add a fullscreen Canvas element underneath everything, drawing a deep forest starfield background with slowly drifting fireflies. Also write three synthesized sound effect functions using Web Audio API: a low selection sound, a paper-flip sound, and a mysterious music box chord for when the reading begins."

**Outcome:** Firefly system (sinusoidal brightness pulsing, independent phase/speed per firefly), green mist dust band on offscreen canvas, three Web Audio synthesizers using OscillatorNode — no external audio files.

---

## Step 4 — AI API Integration & Streaming Output

**Goal:** Connect drawn cards to an LLM reading with real-time text rendering.

> "Add a settings panel for users to input a DeepSeek API key stored in localStorage. When the user selects 3 cards and holds an open palm, trigger the reading. Combine the three drawn cards into a prompt, call the model via fetch, and render the streaming output with a typewriter effect in a modal."

**Outcome:** DeepSeek streaming API integration, rAF-throttled render during stream (`textContent`), single Markdown parse on completion to eliminate flickering. API key stored only in localStorage — never transmitted to any server other than DeepSeek directly.

---

## Step 5 — UX Refinements (Round 1)

Iterative fixes after first full playthrough:

- Card spacing increased; card size enlarged in carousel
- Game start: open palm held for 3 seconds triggers game launch (instead of button click)
- Opening animation: cards fly in from left, spread into carousel
- Scroll speed scales with distance from screen edge
- Fist hold increased to 1 second; visual progress bar + particle feedback added
- After 3 cards drawn: close-up zoom of each card before transitioning to reading trigger

---

## Step 6 — Visual Polish & Atmosphere

**Goal:** Replace generic dark UI with a coherent forest/Art Nouveau identity.

- Modal border replaced with hand-drawn SVG floral vine illustration
- Background shifted from solid black to deep green with fog layers
- Particle effects changed from generic sparks to falling leaf emojis (🍃🍂🌿) on hand movement; petal emojis (✿❀🌸) during card charging; green-gold sparks on card selection
- Firefly system rebuilt: 55 fireflies with sin-wave brightness, yellow-green glow + bright core, fully independent phases and velocities
- Card size in playing field enlarged; inter-card gap increased to at least one card-width

**AI prompt engineering updated:**
- System prompt rewritten to blend Jungian psychology and narrative therapy
- Reading structured into three sections: poetic card interpretation → psychological reflection → actionable guidance
- User's typed question and selected topic fed into prompt for personalized, grounded readings (not generic card meanings)

---

## Step 7 — Privacy, History & Question Input

**Goal:** Make the app trustworthy and replayable.

- Privacy notice added to settings modal: camera processed locally, API key in localStorage only, no third-party servers
- Direct link to DeepSeek API key registration page added in settings
- History system: last 30 readings saved to localStorage with date, question, cards drawn, and full AI interpretation; expandable/deletable entries
- Question input enhanced: topic buttons (Career / Love / Spirituality / Daily) pre-fill the textarea and inject topic-specific prompt direction to the LLM

---

## Step 8 — Bug Fixes & Final Refinements

- Drawn cards removed from deck — no repeats possible across a session
- Card closest to center scales up; selected card shakes briefly before flip
- Close-up card display added: after selection, card zooms to center, shakes, then flips to reveal face before settling into the tray
- AI prompt deepened: poetic opening + realistic psychological layer; reading addresses the user's specific question, not just abstract card symbolism
- Markdown symbols (`*`, `#`) stripped from streaming output
- Firefly brightness and glow radius increased for more visible atmosphere
- Language selector added before reading: Chinese or English; LLM instructed with hard language constraint to prevent mixing

---

## Step 9 — Three-Card Close-Up Reveal Screen

**Goal:** Add a cinematic moment between card selection and the reading stage.

After all three cards are drawn, a full-screen overlay fades in showing all three cards at larger size with position labels (Past / Present / Future), staggered reveal animation with flip sounds and spark bursts, ambient glow orbs, and a pulsing hint text. Auto-transitions to the showcase layer after ~4 seconds.

This was added as a dedicated `triggerTripleCloseup()` function inserted between `drawCurrentCard()` and `triggerRevealSequence()`, with language-aware labels and proper cleanup on reading close.

---

## Artwork

All 78 card illustrations were designed personally in Alphonse Mucha's Art Nouveau style using Gemini image generation, with the following prompt direction:

> "Generate tarot cards in Art Nouveau style featuring beautiful female figures whose character matches the card's symbolic role. Delicate, elegant color palette. Alphonse Mucha style. Fingers clear and correct, soft even lighting, emphasizing the subject's graceful expression and the fine texture of the florals. Romantic, vintage decorative art atmosphere. Standard tarot card proportions, portrait orientation, perfect composition, ultra-high resolution. No Chinese characters in the image."

Cards generated individually across all 22 Major Arcana and 56 Minor Arcana.
