# Accessibility & WCAG 2.2 Compliance

## Target Standard

This site targets **WCAG 2.2 Level AA** compliance.

---

## Colour Palette & Contrast Ratios

All text and UI-component colour pairs were audited against WCAG 2.2 success criteria using the [relative luminance formula](https://www.w3.org/TR/WCAG22/#dfn-relative-luminance).

| Token | Hex | Role |
|---|---|---|
| `primary` | `#004ac6` | Brand blue – headings, active links, buttons |
| `on-primary` | `#ffffff` | Text on primary buttons |
| `on-surface` | `#191b23` | Primary body text |
| `on-surface-variant` | `#434655` | Secondary/muted body text |
| `secondary` | `#515f74` | Muted blue-grey – timeline past-position dots |
| `outline` | `#737686` | Form control borders, timeline line |
| `surface` / `background` | `#faf8ff` | Page background |
| `primary-fixed` | `#dbe1ff` | Badge/chip backgrounds |
| `on-primary-fixed-variant` | `#003ea8` | Text on `primary-fixed` chips |
| `secondary-container` | `#d5e3fc` | Tag/badge backgrounds |
| `on-secondary-fixed-variant` | `#3a485b` | Text on `secondary-container` tags |

### Key contrast pairs (WCAG AA)

| Foreground | Background | Ratio | Criterion |
|---|---|---:|---|
| `on-surface` `#191b23` | `background` `#faf8ff` | **16.3 : 1** | ✅ 4.5 : 1 normal text |
| `on-surface-variant` `#434655` | `background` `#faf8ff` | **8.9 : 1** | ✅ 4.5 : 1 normal text |
| `primary` `#004ac6` | `background` `#faf8ff` | **7.1 : 1** | ✅ 4.5 : 1 normal text |
| `on-primary` `#ffffff` | `primary` `#004ac6` | **7.5 : 1** | ✅ 4.5 : 1 normal text |
| `on-primary-fixed-variant` `#003ea8` | `primary-fixed` `#dbe1ff` | **7.2 : 1** | ✅ 4.5 : 1 normal text |
| `on-secondary-fixed-variant` `#3a485b` | `secondary-container` `#d5e3fc` | **7.2 : 1** | ✅ 4.5 : 1 normal text |
| `outline` `#737686` | `white` `#ffffff` | **4.5 : 1** | ✅ 3 : 1 UI component (form borders) |
| `secondary` `#515f74` | `white` `#ffffff` | **6.5 : 1** | ✅ 3 : 1 UI component (timeline dots) |

---

## Typography Scale

| Element | Font | Size | Weight | Line-height |
|---|---|---|---|---|
| `body` | Inter | 1 rem (16 px) | 400 | 1.5 |
| `h1` | Manrope | 3–4.5 rem | 800 (extrabold) | 1.1 |
| `h2` | Manrope | 2–2.5 rem | 800 (extrabold) | 1.2 |
| `h3` | Manrope | 1.25 rem | 700 (bold) | — |
| Body paragraphs | Inter | 1 rem | 400 | 1.625 (leading-relaxed) |
| Labels / small | Inter | 0.875 rem | 600–700 (semibold/bold) | — |
| Code chips | JetBrains Mono | 0.875 rem | 700 | — |

- No font weight lighter than 400 is used for body text.
- Large text (≥ 18 pt / 24 px, or ≥ 14 pt / ~18.6 px bold) only needs a 3 : 1 ratio.

---

## Focus / Keyboard Navigation

- All interactive elements (`<a>`, `<button>`) expose a **2 px solid `#004ac6` outline** on `:focus-visible` (ratio 7.5 : 1 on white/near-white backgrounds).
- Form inputs use `focus:ring-2 focus:ring-primary focus:border-primary` (Tailwind).
- The page is navigable end-to-end by keyboard in logical DOM order; no `tabindex` traps exist.

---

## How to Verify Contrast

### Browser tools
- **Chrome / Edge DevTools** → Inspect an element → *Accessibility* pane → contrast ratio displayed automatically.
- **Firefox DevTools** → *Accessibility* tab → *Check for issues* → *Contrast*.

### Online tools
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Colour Contrast Analyser (desktop app)](https://www.tpgi.com/color-contrast-checker/)
- [APCA Contrast Calculator](https://www.myndex.com/APCA/) (for WCAG 3 / informational)

### Automated audit
Run an **axe** audit in the browser console:

```js
// In Chrome DevTools console (requires the axe browser extension, or inject axe-core)
axe.run().then(r => console.log(r.violations));
```

Or use the [axe DevTools](https://www.deque.com/axe/devtools/) browser extension for a one-click full-page audit.

### Keyboard navigation test
1. Reload the page and press `Tab` to move focus forward through interactive elements.
2. Verify each focused element has a clearly visible outline.
3. Press `Enter` / `Space` to activate buttons and links.
4. Press `Shift+Tab` to move focus backward.

---

## WCAG Success Criteria Addressed

| SC | Title | Status |
|---|---|---|
| 1.4.3 | Contrast (Minimum) | ✅ AA |
| 1.4.11 | Non-text Contrast | ✅ AA (form borders, timeline indicators) |
| 1.4.4 | Resize Text | ✅ (rem-based sizing) |
| 1.4.1 | Use of Colour | ✅ (links not identified by colour alone) |
| 2.4.7 | Focus Visible | ✅ (focus-visible outlines) |
| 2.4.3 | Focus Order | ✅ (logical DOM order) |
