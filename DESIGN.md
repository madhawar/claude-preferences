# Cloud Dancer — Design System

> PANTONE 11-4201 · 2026 Color of the Year · Quiet Luxury Aesthetic

---

## Concept

Cloud Dancer is a lofty, billowy white imbued with serenity. As a design system it is structural — white provides the scaffolding; everything else is a nuanced neutral shift that dissolves gently into shadow. The mood is **measured consideration and quiet reflection**, not minimalism for minimalism's sake.

North star: **calm, never cold. White-forward, never sterile. Editorial, never corporate.**

---

## Palette

| Token | Hex | Role |
|---|---|---|
| Cloud Dancer | `#F0EEE9` | Hero white — primary page/canvas background |
| Pure Drift | `#FBFAF7` | Lifted surfaces, cards, paper |
| Linen Mist | `#E6E2DA` | Subtle section fills, tints |
| Warm Greige | `#D6D0C6` | Hairlines, borders, structural dividers |
| Pale Stone | `#BDB6AB` | Muted UI, disabled states |
| Soft Taupe | `#8C857A` | Secondary / supporting text |
| Shadow Ash | `#6B6459` | Deep contrast accent — where the white dissolves |
| Ink Slate | `#3A3631` | Primary text (soft near-black, never `#000`) |
| Veil Blush | `#EDE2DD` | Optional pastel accent — warm |
| Veil Sky | `#DEE4E4` | Optional pastel accent — cool |

**Pairing logic:** Cloud Dancer is the ground. Linen Mist and Warm Greige provide tonal layering. Shadow Ash and Ink Slate supply the contrast. Veil Blush or Veil Sky may appear once per composition — never both, never saturated.

---

## Typography

| Role | Font | Weight | Notes |
|---|---|---|---|
| Display / H1–H3 | Cormorant Garamond | 300–400 | Large, light, high-contrast strokes |
| Body / UI | DM Sans | 300–400 | Warm geometric, never cold |
| Captions / Labels | DM Sans | 300 | Uppercase, tracked ~0.20em |

**Critical rule: no weight above 500 anywhere.** Cloud Dancer dies under bold. The serenity lives in thin strokes and generous line-height.

Google Fonts import:
```
https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap
```

---

## CSS Tokens

```css
:root {
  /* palette */
  --cd-cloud:  #F0EEE9;
  --cd-drift:  #FBFAF7;
  --cd-linen:  #E6E2DA;
  --cd-greige: #D6D0C6;
  --cd-stone:  #BDB6AB;
  --cd-taupe:  #8C857A;
  --cd-ash:    #6B6459;
  --cd-ink:    #3A3631;
  --cd-blush:  #EDE2DD;
  --cd-sky:    #DEE4E4;

  /* semantic */
  --cd-bg:          var(--cd-cloud);
  --cd-surface:     var(--cd-drift);
  --cd-text:        var(--cd-ink);
  --cd-text-muted:  var(--cd-taupe);
  --cd-accent:      var(--cd-ash);
  --cd-border:      rgba(58, 54, 49, 0.10);
  --cd-hairline:    rgba(58, 54, 49, 0.16);

  /* typography */
  --cd-font-display: 'Cormorant Garamond', Georgia, serif;
  --cd-font-body:    'DM Sans', system-ui, sans-serif;

  /* shape & depth */
  --cd-radius:      14px;
  --cd-radius-sm:   8px;
  --cd-shadow:      0 18px 50px -28px rgba(58, 54, 49, 0.28);
  --cd-shadow-soft: 0 8px 30px -22px rgba(58, 54, 49, 0.30);
  --cd-space:       clamp(1.5rem, 4vw, 4rem);
}
```

---

## Design Principles

1. **White-forward and airy.** The background is always Cloud Dancer or a softer neutral tint. Negative space is not empty — it is the design.
2. **Restraint on weight.** Light type only. The calm lives in thin strokes. Avoid bold, heavy borders, and hard boxes.
3. **One quiet signature per piece.** One oversized serif headline, one hairline rule, one tonal photograph. Everything else stays still.
4. **Tonal depth over borders.** Prefer soft warm shadows and tonal washes. The signature divider is a single Warm Greige hairline. Contrast comes from the palette dissolving into Shadow Ash — not from borders.
5. **Soft geometry.** Border-radius 8–18px or crisp gallery-square. No playful bubbles, no heavy outlines.
6. **Text is soft-dark, never black.** Ink Slate `#3A3631` for body. Soft Taupe for secondary. Never pure `#000`.
7. **Color is a guest.** If a hue is needed, one muted pastel (Veil Blush or Veil Sky) may appear briefly — never compete with the white, never both at once.

---

## Accessibility

| Pairing | Contrast | Use |
|---|---|---|
| Ink Slate on Cloud Dancer | ~9:1 | Body text — safe |
| Ink Slate on Pure Drift | ~9:1 | Card body text — safe |
| Shadow Ash on Cloud Dancer | ~4.5:1 | Large text / UI only |
| Soft Taupe on Cloud Dancer | ~3:1 | Large secondary text only |
| Pure Drift on Shadow Ash | ~4.5:1 | Button text on ash background |

- Never use Pale Stone, Warm Greige, or Veil tones for reading text on white.
- Respect `prefers-reduced-motion`.
- Focus rings: 2px solid Shadow Ash `#6B6459`, offset 3px.

---

## Image Generation (ChatGPT / DALL·E / Midjourney)

**Palette phrasing:**
> "warm off-white Cloud Dancer palette (#F0EEE9), linen and greige neutrals dissolving into soft shadow-ash, at most one whisper of muted pastel (warm blush or cool sky), never saturated"

**Negative cues:**
> "no bright or saturated colors, no neon, no pure black, no high contrast, no clutter, no busy backgrounds, no bold text overlays"

**Prompt formula:** Subject → generous negative space → Cloud Dancer palette phrasing → soft diffused natural daylight → serene / quiet-luxury / editorial mood → fine grain / soft focus → negative cues.

---

## Voice & Tone

- Unhurried. Never urgent.
- Sparse. Say less. Mean more.
- Warmth without enthusiasm.
- No exclamation marks. No superlatives.
